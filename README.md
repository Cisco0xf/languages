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
   const Map<LanguageCode, RegExp> languageRegExp = {
    LanguageCode.en: RegExp(r'[a-zA-Z]'),
    LanguageCode.ar: RegExp(r'[\u0600-\u06FF]'),
    // ...language-specific regex patterns
   };
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

