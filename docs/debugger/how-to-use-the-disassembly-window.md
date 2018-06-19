---
title: Wyświetlanie kodu dezasemblacji w debugerze programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 46c0ae689a9d514983aeb747bebc6cb9905c6e11
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475538"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger"></a>Wyświetlanie kodu dezasemblacji w debugerze programu Visual Studio
Ta funkcja jest dostępna tylko wtedy, gdy włączone jest debugowanie poziomie adresu **opcje** okno dialogowe **debugowanie** węzła. Nie jest niedostępna na potrzeby debugowania skryptu lub SQL.  
  
 **Dezasemblacji** okna zawiera kod zestawu odpowiadający instrukcje utworzony przez kompilator. Jeśli debugowania kodu zarządzanego w instrukcjach zestawu odpowiadają kodu natywnego utworzone za pomocą kompilatora Just in Time (JIT), nie Microsoft język pośredni (MSIL) generowane przez kompilator Visual Studio.  
  
 Oprócz instrukcje zestawu **dezasemblacji** okna można wyświetlić następujące informacje opcjonalne:  
  
-   Adres pamięci, gdzie znajduje się każdej instrukcji. Dla natywnych aplikacji jest to adres pamięci rzeczywistych. Visual Basic, C# lub kodu zarządzanego jest przesunięcie od początku funkcji.  
  
-   Kod źródłowy, z którego pochodzi kodu zestawu.  
  
-   Kod bajtów — reprezentacje bajtów rzeczywiste maszyny lub instrukcje MSIL.  
  
-   Nazwy symboli dla adresów pamięci.  
  
-   Numery wierszy odpowiadających kodu źródłowego.  
  
 Język asemblera instrukcje składają się z klawiszy skrótu skrótów nazw instrukcji oraz symbole, reprezentujących zmienne, rejestrów i stałe. Każdą instrukcję języka maszyny jest reprezentowany przez wartość jednego języka zestawu, zazwyczaj następuje jeden lub więcej zmiennych, rejestrów lub stałe.  
  
 Nie można odczytać języka zestawu, aby w pełni korzystać z okna dezasemblacji można znaleźć dobrej książki na programowania w języku języka zestawu. Język asemblera programowania jest poza zakres co można rozwiązać w to krótkie wprowadzenie do okna dezasemblacji.  
  
 Ponieważ kodu zestawu w dużym stopniu korzysta z rejestrów procesora lub, w przypadku kodu zarządzanego, rejestruje środowisko uruchomieniowe języka wspólnego, często znajduje się on umożliwia korzystanie z okna dezasemblacji w połączeniu z okna rejestrów, dzięki czemu można zbadać rejestru zawartość.  
  
 Prawdopodobnie będzie nigdy nie masz desire lub konieczne wyświetlenie kod maszynowy instrukcje w swoich pierwotnych, numerycznego formularza, a nie języka zestawu. Jednak jeśli chcesz to zrobić, możesz do tego celu użyć okna pamięci lub wybrać bajtów kodu z menu skrótów w oknie dezasemblacji.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-display-the-disassembly-window"></a>Aby wyświetlić okno dezasemblacji  
  
-   Podczas debugowania, wybierz **Debuguj > Windows** , a następnie kliknij przycisk **dezasemblacji**.
  
### <a name="to-turn-optional-information-on-or-off"></a>Aby włączyć opcjonalne informacje lub wyłączyć  
  
-   Kliknij prawym przyciskiem myszy **dezasemblacji** okno i ustawić lub wyczyścić wybrane opcje w menu skrótów.  
  
     Żółta strzałka na lewym marginesie oznacza lokalizację bieżącego punktu wykonywania. Dla kodu natywnego odpowiada licznik programu Procesora. Ta lokalizacja zawiera następną instrukcję, która zostanie wykonana w programie.  
  
     Aby uzyskać więcej informacji, zobacz [stronicowanie w górę lub w dół w pamięci](../debugger/how-to-page-up-or-down-in-memory.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)   
 [Porady: Korzystanie z okna rejestrów](../debugger/how-to-use-the-registers-window.md)