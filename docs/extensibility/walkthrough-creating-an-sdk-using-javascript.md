---
title: "Wskazówki: Tworzenie SDK przy użyciu języka JavaScript | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2a53b10f3d9a69c0181a432dad491bebd177f5be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-sdk-using-javascript"></a>Wskazówki: Tworzenie SDK przy użyciu języka JavaScript
Ten przewodnik zawiera wskazówki Tworzenie prostego matematyczne SDK jako Visual Studio rozszerzenia (VSIX) przy użyciu języka JavaScript.  Instruktaż jest podzielona na następujące elementy:  
  
-   [Aby utworzyć projekt zestawu SDK rozszerzenia SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)  
  
-   [Do tworzenia przykładowej aplikacji, która korzysta z zestawu SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)  
  
 Dla języka JavaScript Brak typu projektu biblioteki klas. W tym przewodniku przykładowy plik arithmetic.js jest tworzone bezpośrednio w pliku VSIX projektu. W praktyce, zaleca się najpierw skompilować i pliki obsługi języka JavaScript i CSS testu jako aplikacji ze Sklepu Windows — na przykład za pomocą **pusta aplikacja** szablonu — przed wprowadzeniem w projekcie VSIX.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby użyć tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createSimpleMathVSIX"></a>Aby utworzyć projekt zestawu SDK rozszerzenia SimpleMathVSIX  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  Na liście Kategorie szablonów w obszarze **Visual C#**, wybierz pozycję **rozszerzalności**, a następnie wybierz **projektu VSIX** szablonu.  
  
3.  W **nazwa** tekst Określ `SimpleMathVSIX` i wybierz polecenie **OK** przycisku.  
  
4.  Jeśli **Kreatora pakietu Visual Studio** zostanie wyświetlona, wybierz **dalej** znajdującego się na **-Zapraszamy** strony, a następnie na **strona 1, 7**, wybierz **Zakończ** przycisku.  
  
     Mimo że **projektanta manifestu** zostanie otwarta, firma Microsoft będzie przechowywać tego przewodnika prostego przez bezpośrednie modyfikowanie pliku manifestu.  
  
5.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla pliku source.extension.vsixmanifest, a następnie wybierz **kod widoku**. Użyj tego kodu zastąpić istniejącą zawartość w pliku.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
      <Metadata>  
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />  
        <DisplayName>Simple Math</DisplayName>  
        <Description>Does basic arithmetic calculations.</Description>  
      </Metadata>  
      <Installation Scope="Global" AllUsers="true">  
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />  
      </Installation>  
      <Dependencies>  
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />  
      </Dependencies>  
      <Assets>  
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />  
      </Assets>  
    </PackageManifest>  
    ```  
  
6.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu SimpleMathVSIX, a następnie wybierz **Dodaj**, **nowy element**.  
  
7.  W **danych** kategorii, wybierz opcję **pliku XML**, nadaj nazwę plikowi `SDKManifest.xml`i wybierz polecenie **Dodaj** przycisku.  
  
8.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla pliku SDKManifest.xml, a następnie wybierz **Otwórz** do wyświetlenia pliku w **edytora XML**.  
  
9. Dodaj następujący kod do pliku SDKManifest.xml.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <FileList  
      DisplayName="Simple Math"  
      MinVSVersion="14.0"  
      AppliesTo="JavaScript+WindowsAppContainer"  
      SupportsMultipleVersions="Error"  
      MoreInfo="http://www.msdn.microsoft.com/">  
  
      <!-- JS -->  
      <File Content="js\arithmetic.js" />  
    </FileList>  
  
    ```  
  
10. W **Eksploratora rozwiązań**, w menu skrótów dla pliku SDKManifest.xml wybierz **właściwości**.  
  
11. W **właściwości** ustaw **Include w pliku VSIX** właściwości **True**.  
  
12. W **Eksploratora rozwiązań**, w menu skrótów projektu SimpleMathVSIX wybierz **Dodaj**, **nowy Folder**oraz folder o nazwie `Redist`.  
  
13. Dodaj podfoldery Redist tworzenia tej struktury folderów:  
  
     \Redist\CommonConfiguration\Neutral\SimpleMath\js\  
  
14. W menu skrótów do folderu \js\ wybierz **Dodaj**, **nowy element**.  
  
15. W obszarze **elementów Visual C#**, wybierz pozycję **Web** kategorii, a następnie wybierz **plik JavaScript** elementu. Nadaj nazwę plikowi `arithmetic.js`, a następnie wybierz pozycję **Dodaj** przycisku.  
  
16. Wstaw następujący kod do arithmetic.js:  
  
    ```  
    (function (global) {  
        "use strict";  
        global.Arithmetic = {  
            add: function (firstNumber, secondNumber) {  
                return firstNumber + secondNumber;  
            },  
  
            subtract: function (firstNumber, secondNumber) {  
                return firstNumber - secondNumber;  
            },  
  
            multiply: function (firstNumber, secondNumber) {  
                return firstNumber * secondNumber;  
            },  
  
            divide: function (firstNumber, secondNumber) {  
                return firstNumber / secondNumber;  
            }  
        };  
    })(this);  
  
    ```  
  
17. W **Eksploratora rozwiązań**, w menu skrótów dla pliku arithmetic.js wybierz **właściwości**. Należy wprowadzić te zmiany właściwości:  
  
    -   Ustaw **Include w pliku VSIX** właściwości **True**.  
  
    -   Ustaw **Kopiuj do katalogu wyjściowego** właściwości **zawsze Kopiuj**.  
  
18. W **Eksploratora rozwiązań**, w menu skrótów projektu SimpleMathVSIX wybierz **kompilacji**.  
  
19. Po zakończeniu kompilacji pomyślnie, w menu skrótów projektu, wybierz **Otwórz Folder w Eksploratorze plików**. Przejdź do \bin\debug\\i uruchom `SimpleMathVSIX.vsix` go zainstalować.  
  
20. Wybierz **zainstalować** przycisk i umożliwiają zakończenie instalacji.  
  
21. Uruchom ponownie program Visual Studio.  
  
##  <a name="createSampleApp"></a>Do tworzenia przykładowej aplikacji, która korzysta z zestawu SDK  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  Na liście Kategorie szablonów w obszarze **JavaScript**, wybierz pozycję **Sklepu Windows**, a następnie wybierz **pusta aplikacja** szablonu.  
  
3.  W **nazwa** określ `ArithmeticUI`. Wybierz **OK** przycisku.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu ArithmeticUI, a następnie wybierz **Dodaj**, **odwołania**.  
  
5.  W obszarze **Windows**, wybierz **rozszerzenia**i zwróć uwagę, że **proste matematyczne** jest wyświetlany.  
  
6.  Wybierz **proste matematyczne** pole wyboru, a następnie wybierz pozycję **OK** przycisku.  
  
7.  W **Eksploratora rozwiązań**w obszarze **odwołania**, zwróć uwagę, że **proste matematyczne** odwołania jest wyświetlony. Rozwiń go i zwróć uwagę, czy znajduje się folder \js\, który zawiera arithmetic.js. Można także otworzyć arithmetic.js, aby upewnić się, że kod źródłowy został zainstalowany.  
  
8.  Użyć poniższego kodu, aby zastąpić zawartość default.htm.  
  
    ```  
    <!DOCTYPE html>  
    <html>  
    <head>  
        <meta charset="utf-8" />  
        <title>ArithmeticUI</title>  
  
        <!-- WinJS references -->  
        <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />  
        <script src="//Microsoft.WinJS.1.0/js/base.js"></script>  
        <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>  
  
        <!-- ArithmeticUI references -->  
        <link href="/css/default.css" rel="stylesheet" />  
        <script src="/js/default.js"></script>  
        <script src="/SimpleMath/js/arithmetic.js"></script>  
    </head>  
    <body>  
        <form>  
        <div id="calculator" class="ms-grid">  
            <input name="firstNumber" id="firstNumber" type="number" step="any">  
            <div id="operators">  
                <button class="operator" type="button">+</button>  
                <button class="operator" type="button">-</button>  
                <button class="operator" type="button">*</button>  
                <button class="operator" type="button">/</button>  
            </div>  
            <input id="secondNumber" type="number">  
            <button class="calculate" type="button">=</button>  
            <input id="result" type="number" name="result" disabled="" readonly="">  
        </div>  
        </form>  
    </body>  
    </html>  
    ```  
  
9. Umożliwia zastępowanie zawartości \js\default.js kolejnego kodu.  
  
    ```  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var operation = null;  
  
        function calculateResult() {  
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),  
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),  
                result = 0;  
  
            if (isNaN(firstNumber) || isNaN(secondNumber)) {  
                result = 0;  
            }  
            else {  
                switch (operation) {  
                    case "+":  
                        result = Arithmetic.add(firstNumber, secondNumber);  
                        break;  
                    case "-":  
                        result = Arithmetic.subtract(firstNumber, secondNumber);  
                        break;  
                    case "*":  
                        result = Arithmetic.multiply(firstNumber, secondNumber);  
                        break;  
                    case "/":  
                        result = Arithmetic.divide(firstNumber, secondNumber);  
                        break;  
                    default:  
                }  
            }  
            document.querySelector("#result").value = result.toString();  
        }  
  
        app.onactivated = function (args) {  
            document.querySelector("#calculator").addEventListener("click", function (event) {  
                if (event.target.tagName.toLowerCase() === "button") {  
                    switch (event.target.className) {  
                        case "operator":  
                            operation = event.target.innerText;  
                            break;  
                        case "calculate":  
                            calculateResult();  
                            break;  
                        default:  
                            break;  
                    }  
                }  
            });  
        };  
  
        app.start();  
    })();  
    ```  
  
10. Zastąp zawartość \css\default.css ten kod:  
  
    ```  
    form {  
        display: -ms-grid;  
        -ms-grid-rows: 1fr auto 1fr;  
        -ms-grid-columns: 1fr auto 1fr;  
        height: 100%;  
        width: 100%;  
    }  
  
    button, input[type=number] {  
        margin-right: 5px;  
        -ms-grid-row-align: center;  
    }  
  
    #calculator {  
        -ms-grid-column: 2;  
        -ms-grid-row: 2;  
        display: -ms-grid;  
        -ms-grid-rows: 1fr;  
        -ms-grid-columns: auto min-content auto auto auto;  
    }  
  
    .ms-grid input {  
        width: 5em;  
    }  
  
    #firstNumber {  
        -ms-grid-column: 1;  
        -ms-grid-row-align: center;  
    }  
  
    #operators {  
        -ms-grid-column: 2;  
        -ms-grid-row-align: center;  
    }  
  
        #operators button.operator {  
            margin-bottom: 5px;  
            height: 40px;  
        }  
  
    #secondNumber {  
        -ms-grid-column: 3;  
    }  
  
    button.calculate {  
        -ms-grid-column: 4;  
        -ms-grid-row-align: center;  
        height: 40px;  
    }  
  
    #result {  
        -ms-grid-column: 5;  
    }  
  
    ```  
  
11. Wybierz klawisz F5, aby skompilować i uruchomić aplikację.  
  
12. W aplikacji interfejsu użytkownika, wprowadź wszelkie dwóch liczb, wybierz operację, a następnie wybierz  **=**  przycisku. Zostanie wyświetlone prawidłowego wyniku.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie zestawu SDK](../extensibility/creating-a-software-development-kit.md)