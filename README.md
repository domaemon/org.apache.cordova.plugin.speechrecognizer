This software is heavily based on the work of https://github.com/poiuytrez/SpeechRecognizer

The repository name was changed to support the Cordova plugin CLI installation.

Android SpeechRecognizer plugin for Cordova/Phonegap
===================================
This plugin provides access to the speech recognition feature. This plugin will recognize commands, phrases, etc as spoken by the user.

![Screenshot speak now](/screenshots/speaknow.png "Speak now")

Requirements
-------------
Android 2.2 (API level 8) is required  
Compatible with Cordova 3.0.

Support
---------------------
For free community support, please use the issue tracker.  
To get professional non-free support for the plugin, please contact me at gcharhon(at)smartmobilesoftware.com.

Installation 
-------------
1) cordova plugin add https://github.com/domaemon/org.apache.cordova.plugin.speechrecognizer.git
2) call navigator.SpeechRecognizer object from your javascript (see below for an example).

Usage
-------

#### Start recognition
Show the recognition dialog and get the recognized sentences

    SpeechRecognizer.startRecognize(success, error, maxMatches, promptString, language);
parameters
* success : The success callback. It provides a json array with all possible matches. Example: "[hello world,low world,hello walls]".
* error : The error callback.
* maxMaches : Maximum of returned possibles sentences matches.
* promptString : String shown below the Google logo and the microphone icon. Instruct the user of what to. Example: "Speak now"
* language : Language used by the speech recognition engine. Example: "en-US".

#### Supported languages
Get the list of supported languages codes

    SpeechRecognizer.getSupportedLanguages(success, error);
parameters
* success : The success callback. It provides a json array of all the recognized language codes. Example: "[en-US,fr-FR,de-DE]".
* error : The error callback.

Full example
----------------
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Speech Recognition plugin demo</title>
        <script type="text/javascript" src="cordova-2.8.js"></script>
        <script type="text/javascript" src="SpeechRecognizer.js"></script>
    </head>
    <body>

        <script type="text/javascript">

            function onDeviceReady(){
                console.log("Device is ready");
            }

            function recognizeSpeech() {
                var maxMatches = 5;
                var promptString = "Speak now";	// optional
                var language = "en-US";						// optional
                navigator.SpeechRecognizer.startRecognize(function(result){
                    alert(result);
                }, function(errorMessage){
                    console.log("Error message: " + errorMessage);
                }, maxMatches, promptString, language);
            }

            // Show the list of the supported languages
            function getSupportedLanguages() {
                navigator.SpeechRecognizer.getSupportedLanguages(function(languages){
                    // display the json array
                    alert(languages);
                }, function(error){
                    alert("Could not retrieve the supported languages : " + error);
                });
            }

            document.addEventListener("deviceready", onDeviceReady, true);
        </script>

        <button onclick="recognizeSpeech();">Start recognition</button>
        <button onclick="getSupportedLanguages();">Get Supported Languages</button>
    </body>
</html>
```

License
----------------

The MIT License

Copyright (c) 2011-2013  
Colin Turner (github.com/koolspin)  
Guillaume Charhon (github.com/poiuytrez)  

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
