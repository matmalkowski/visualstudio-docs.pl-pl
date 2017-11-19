---
title: Wprowadzenie do korzystania z diagnostyki grafiki programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 05/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59131181-1caa-4b7f-be4b-e84709634edf
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 577fd16d93bdfd1ad15bb3469495fdd1342a6994
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Wprowadzenie do korzystania z diagnostyki grafiki programu Visual Studio
W tej sekcji umożliwią przygotowanie do użycia diagnostyki grafiki po raz pierwszy, a następnie należy przechwycić ramki z aplikacji Direct3D i sprawdzić ich w analizatorze grafiki.  
  
## <a name="requirements"></a>Wymagania  
 Aby użyć diagnostyki grafiki w programie Visual Studio, należy użyć programu Visual Studio Enterprise, Visual Studio Professional i Visual Studio Community.  Inne wersje, w tym Visual Studio Code, nie zawierają tej funkcji.
 
 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]  
  
### <a name="windows-10-prerequisites"></a>Wymagania wstępne systemu Windows 10  
 Opcjonalna funkcja Windows *narzędzi graficznych* udostępnia infrastrukturę przechwytywania i odtwarzania, która jest wymagana przez diagnostyki grafiki w systemie Windows 10.  
  
 Aby uzyskać informacje na temat instalowania narzędzi graficznych, zobacz [zainstalować graficznych narzędzi dla systemu Windows 10](#InstallGraphicsTools).  
  
### <a name="windows-81-prerequisites"></a>Wymagania wstępne Windows 8.1  
 Windows Software Development Kit (SDK) dla Windows 8.1 udostępnia infrastrukturę przechwytywania i odtwarzania, która jest wymagana przez diagnostyki grafiki na Windows 8.1 i obsługuje programowanie dla Windows 8.1 i Windows 8.  
  
 [Pobierz zestaw Windows Software Development Kit (SDK) dla Windows 8.1](https://msdn.microsoft.com/en-us/windows/desktop/bg162891.aspx)  
  
 Aby użyć zdalną maszynę odtwarzającą z systemem Windows 10 z programowanie komputera z uruchomionym systemem Windows 8.1, należy zainstalować zestaw Windows 10 SDK na komputerze deweloperskim i na maszynie odtwarzającej opcjonalna funkcja narzędzi graficznych.  
  
##  <a name="InstallGraphicsTools"></a>Instalowanie narzędzi graficznych dla systemu Windows 10  
 W systemie Windows 10 infrastruktury diagnostyki grafiki są dostarczane przez opcjonalna funkcja systemu Windows o nazwie *narzędzi graficznych*. Ta funkcja jest wymagana do przechwytywania i odtwarzanie informacji graficznych w systemie Windows 10, niezależnie od tego, czy aplikacja przechwytywanym obiektów docelowych poprzedniej wersji systemu windows lub używa wersji programu Direct3D. Można wybrać opcję instalacji funkcja narzędzi graficznych wcześniejsze; w przeciwnym razie będzie zainstalowana na żądanie pierwszy uruchomieniu sesji diagnostyki grafiki w programie Visual Studio.  
  
#### <a name="to-install-graphics-tools-for-windows-10"></a>Aby zainstalować narzędzi graficznych dla systemu Windows 10  
  
1.  W polu Wyszukaj wpisz **aplikacje i funkcje** , a następnie otwórz **aplikacje i funkcje** ustawienia.
  
3.  Po prawej stronie **aplikacje i funkcje** okno dialogowe, wybierz **opcjonalne funkcje zarządzania** (w obszarze **aplikacje i funkcje**).

    **Opcjonalne funkcje zarządzania** zostanie wyświetlone okno dialogowe.
  
4.  W **opcjonalne funkcje zarządzania** okno dialogowe, wybierz **Dodawanie funkcji**. Zostanie wyświetlona lista funkcji opcjonalnych, które można zainstalować.  
  
5.  Wybierz **narzędzi graficznych** z listę funkcji, a następnie wybierz **zainstalować**.  
  
 Funkcja narzędzi graficznych jest również instalowany automatycznie podczas instalacji zestawu Windows 10 SDK.  
  
> [!TIP]
>  Opcjonalna funkcja narzędzi graficznych systemu Windows 10 udostępnia lekkie przechwytywania i odtwarzania funkcje — takie jak program przechwytywania wiersza polecenia **dxcap.exe**— które mogą być używane w pomocy technicznej, testowanie i scenariuszami diagnostyki maszyny, na którym nie są zainstalowane narzędzia dla deweloperów. Aby uzyskać więcej informacji, zobacz [przechwytywania narzędzie wiersza polecenia](command-line-capture-tool.md) tematu.  
  
## <a name="using-graphics-diagnostics-for-the-first-time"></a>Używanie diagnostyki grafiki po raz pierwszy  
 Teraz, gdy masz wszystko, czego potrzebujesz, możesz rozpocząć korzystanie z diagnostyki grafiki. Wykonaj następujące kroki.  
  
### <a name="1---create-a-direct3d-app"></a>1 — Tworzenie aplikacji Direct3D  
 Jeśli masz już własną aplikację Direct3D, aby eksplorować diagnostyki grafiki, ponosić! W przeciwnym razie użyj jednej z następujących czynności:

- **Programu DirectX 11 (uniwersalna aplikacja systemu Windows)** lub **DirectX 12 (uniwersalna aplikacja systemu Windows)** szablony projektu dla systemu Windows 10.
- **Aplikacji DirectX (Windows 8.1)** szablonu projektu dla Windows 8.1.
- [Przykładowe Direct3D 12 UAP](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) dla systemu Windows 10.  
- [Próbki gier Marmur Labirynt DirectX](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345) dla Windows 8.1.  
  
 Upewnij się, że można tworzyć aplikacji przed kontynuowaniem.  
  
### <a name="2---start-a-graphics-diagnostics-session"></a>2 - rozpocząć sesję diagnostyki grafiki  
 Teraz możesz rozpocząć sesję diagnostyki grafiki pierwszy. W programie Visual Studio, w menu głównym wybierz **debugowania, grafiki, Rozpocznij debugowanie grafiki**, lub od razu naciśnij **Alt + F5**. Uruchamia aplikację pod nadzorem diagnostyki grafiki i wyświetla okna sesji diagnostyki w programie Visual Studio.  
  
> [!IMPORTANT]
>  Jeśli korzystasz z aplikacji w systemie Windows 10 i nie został jeszcze zainstalowany opcjonalna funkcja narzędzi graficznych, zostanie wyświetlony monit Zrób to teraz. Należy go zainstalować przed użyciem diagnostyki grafiki w systemie Windows 10.  
  
### <a name="3---capture-frames"></a>3 - przechwycić ramki  
 Wszystko jest gotowe do przechwytywania ramek zaraz po uruchomieniu aplikacji.  
  
#### <a name="to-capture-single-frames"></a>Aby przechwycić jednego klatek  
  
-   W programie Visual Studio, wybierz **przechwycić ramki** przycisk z okna sesji paska narzędzi lub diagnostyki grafiki. Lub, jeśli aplikacja ma fokus, wystarczy nacisnąć klawisz **Print Screen** klucza na klawiaturze.
  
#### <a name="to-capture-a-sequence-of-frames"></a>Aby przechwycić sekwencji ramek  
  
-   W programie Visual Studio, w oknie sesji diagnostycznej ustawić **ramek do przechwycenia** liczbę ramek, które mają być przechwytywane w sekwencji, następnie przechwycić sekwencji za pomocą dowolnej z metod opisanych powyżej do przechwycenia jednego klatek.  
  
     Aby przechwycić ramki pojedynczego ponownie, należy ustawić **ramek do przechwycenia** do *1*.  
  
 Po zakończeniu przechwytywania ramek właśnie zakończyć działanie aplikacji lub wybierz **zatrzymać** przycisk z graficznych narzędzi lub okna sesji diagnostycznej.  
  
### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 - Sprawdź ramki przechwycone w analizatorze grafiki  
 Teraz możesz przystąpić do sprawdzenia ramek, które została przechwycona. Aby rozpocząć, analizowanie ramki, wybierz numer ramki ramki, który chcesz zbadać z okna sesji diagnostycznej. Spowoduje to otwarcie ramkę w **analizatora grafiki**, gdzie można użyć narzędzia diagnostyki grafiki do sprawdzenia, jak Twoja aplikacja korzysta z Direct3D śledzić renderowania problemów, lub **analizy ramek** narzędzia do Dowiedz się, jego wydajność.  
  
 Jeśli wybrano nieprawidłową ramkę w oknie sesji diagnostycznej lub do sprawdzenia innej ramki, można wybrać nową z analizatora grafiki. Na **docelowego renderowania** kartę okna dziennika grafiki w ramach obrazu docelowego renderowania, rozwiń węzeł **listy ramek** , a następnie wybierz innej ramki do sprawdzenia.  
  
 Aby dowiedzieć się więcej na temat narzędzia Analizator grafiki ze sobą, zobacz [przykłady](graphics-diagnostics-examples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Direct3D 12 grafiki](http://msdn.microsoft.com/en-us/52094ae3-3b44-4689-9ee7-1ba1b3a779cb)