# Language Configuration Files

This directory contains all language-related definitions for the `AutoLangField` package.
You can use it to customize the language detection in the package.
Contains the RegExp patterns for +81 language, its Language Code and the language data 

## File Details:

1. `languages_code_enum.dart`:
   ```dart
   enum LanguageCode {
    en,    // English
    ar,    // Arabic
    es,    // Spanish
    // ...80+ supported languages
   }
    ```

2. `languages_regexp.dart`:

   ```dart
   class LanguageRegExp {
       static final RegExp deRegExp = RegExp(
       r'(?:[äöüÄÖÜß]|'
       r'\b(ich|esse|einen|apfel|der|die|das|und|in|den|von|zu|mit|sich|ist|für|auf|ein|eine|nicht|als|auch|er|sie|es|haben|werden|wie|du)\b)',
       caseSensitive: false,
       unicode: true,
        );
      
        /// RegExp for the Japanese language
        /// Language has code => [LanguageCode.ja]
      
        static final RegExp jaRegExp = RegExp(
          r'[\u3040-\u309F\u30A0-\u30FF]' // Hiragana and Katakana
          r'|'
          r'\b(の|に|は|を|が|で|と|た|し|て|です|ます|である|から|まで|より|として|による|について|における|に対して|において|によって|をもって|をめぐって|として|について|における|に関して|に対する|によると)\b'
          r'|'
          r'(の|に|は|を|が|で|と|た|し|て|です|ます|である|から|まで|より|として|による|について|における|に対して|において|によって|これ|それ|あれ|この|その|あの|ここ|そこ|あそこ|だれ|何|どこ|いつ|なぜ|どう|どの|どんな|いくら|いくつ|どれ|どちら)'
          r'|'
          r'(は|が|を|に|で|と|から|まで|より|へ|や|か|も|だけ|しか|など|ほど|くらい|ぐらい|ばかり|だって|って|という|といった|とか|など|なんか|なんて)'
          r'|'
          r'(です|ます|だった|でした|ている|ていた|ていく|てくる|てある|ておく|てみる|てしまう|られる|させる|せる|れる)',
          caseSensitive: false,
          unicode: true,
        );

         /// ... Pther languages RegExp pattern
      
       }
   
   ```

3. `languages_data.dart`:
   ```dart
   const Map<LanguageCode, LanguageData> languagesData = {
      LanguageCode.en: LanguageData(
        langRegExp: languageRegExp[LanguageCode.en]!,
        langName: 'English',
        textDirection: TextDirection.ltr,
      ),
      // ...complete language configurations
    };
    ```
### Interdependencies

## File Relationships

1. **Core Definitions**  
   ▶ `language.dart` → `LanguageCode` enum  
   └─┬ Used as keys in `language_data.dart`

2. **Detection Patterns**  
   ▶ `language_regexp.dart` → Language-specific RegExp  
   └─┬ Injected into `language_data.dart` configurations

3. **Final Export**  
   ▶ `language_data.dart` combines both  
   └─┬ Provides ready-to-use `languagesData` to `AutoLangField`

