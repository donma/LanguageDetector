
With the use of LanguageDetection(https://www.nuget.org/packages/LanguageDetection), language detection can be achieved for most scenarios.

Detail: https://blog.no2don.com/2023/10/c-sharp-detect-language.html


Sample Code:

```cs

           var str = "你好世界,你好世界,Hello World,Bonjour le monde,こんにちは世界,สวัสดีชาวโลก,안녕하세요 세상";

           var detector = new LanguageDetection.LanguageDetector();
           detector.AddAllLanguages();


           //from: https://idsyst.hu/development/language_detector.html
           var lmDetector = new LanguageDetector.LanguageDetector();
           foreach (var r in str.Split(","))
           {

               var checkFirst = detector.Detect(r);
               if (!string.IsNullOrEmpty(checkFirst))
               {
                   if (checkFirst == "zho")
                   {
                       Console.WriteLine(r + "=>" + lmDetector.Detect(r) + "!");
                   }
                   else
                   {
                       Console.WriteLine(r + "=>" + detector.Detect(r));
                   }

               }
               else
               {
                   Console.WriteLine(r + "=>" + lmDetector.Detect(r) + "!");

               }
           }

```


Original Reference: 

Based on the idea and JavaScript code developed by Rich Tibbett (https://github.com/richtr/guessLanguage.js)
 
C# version by Sasvári Tamás https://idsyst.hu/development/language_detector.html
