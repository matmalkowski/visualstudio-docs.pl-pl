---
title: "Wskazówki: Programowe przechwytywanie informacji graficznych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5adeff9-afaf-4047-b5ce-ef0aefe710eb
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2bf34eda9c9957b8a989244da3f2fce03a5d151e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Wskazówki: programowe przechwytywanie informacji graficznych
Można użyć [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagnostyki grafiki do programowe przechwytywanie informacji graficznych z aplikacji Direct3D.  
  
 Przechwycenie programowe jest przydatne w scenariuszach, takich jak:  
  
-   Po swapchain istnieje, np. podczas renderowania jej tekstury nie korzysta z aplikacji grafiki programowo rozpocząć przechwytywania.  
  
-   Po aplikacji nie renderowania, np. gdy DirectCompute jest używane do obliczeń programistycznie rozpocząć przechwytywania.  
  
-   Wywołanie `CaptureCurrentFrame`Jeżeli problem z renderowaniem jest trudne do przewidywania i przechwytywania w testów ręcznych, ale można przewidzieć programowo przy użyciu informacji o stanie aplikacji w czasie wykonywania.  
  
##  <a name="CaptureDX11_2"></a>Przechwycenie programowe w Windows 8.1  
 Ta część przewodnika pokazuje przechwycenie programowe w aplikacji, które używają interfejsu API programu DirectX 11.2 na Windows 8.1, które używa metody przechwytywania niezawodny. Aby uzyskać informacje o sposobie używania przechwycenie programowe w aplikacjach korzystających z wcześniejszych wersji programu DirectX w systemie Windows 8.0, zobacz [przechwycenie programowe w systemie Windows 8.0 i wcześniejsze](#CaptureDX11_1) dalszej części tego przewodnika.  
  
 W tej sekcji przedstawiono sposób wykonywania tych zadań:  
  
-   Przygotowywanie aplikacji do użycia przechwycenie programowe  
  
-   Uzyskiwanie interfejsu IDXGraphicsAnalysis  
  
-   Przechwytywanie informacji graficznych  
  
> [!NOTE]
>  Poprzednich implementacjach przechwycenie programowe zależał od narzędzi Remote Tools for [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] umożliwiają korzystanie z funkcji przechwytywania, Windows 8.1 obsługuje przechwytywanie bezpośrednio za pomocą Direct3D 11.2. W związku z tym nie należy zainstalować narzędzia zdalnej dla przechwycenie programowe na Windows 8.1.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Przygotowywanie aplikacji do użycia przechwycenie programowe  
 Aby użyć przechwycenie programowe w aplikacji, musi on zawierać niezbędne nagłówki. Te nagłówki są częścią zestawu Windows 8.1 SDK.  
  
##### <a name="to-include-programmatic-capture-headers"></a>Aby uwzględnić nagłówki przechwycenie programowe  
  
-   Zawiera tych nagłówków w pliku źródłowym, w którym zostaną zdefiniowane interfejsu IDXGraphicsAnalysis:  
  
    ```  
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    >  Nie dołączaj nagłówka vsgcapture.h—which obsługuje programowe Przechwytywanie plików w systemie Windows 8.0 i wcześniej — w celu wykonania przechwycenie programowe w aplikacji Windows 8.1. Ten nagłówek jest niezgodna z DirectX 11.2. Jeśli ten plik będzie po nagłówek d3d11_2.h jest dołączony, kompilator generuje ostrzeżenie. Jeśli vsgcapture.h znajduje się przed d3d11_2.h, aplikacja nie zostanie uruchomiona.  
  
    > [!NOTE]
    >  Jeśli 2010 czerwca DirectX SDK jest zainstalowany na tym komputerze i zawiera ścieżkę do załączenia projektu `%DXSDK_DIR%includex86`, przenieś go do końca ścieżki include. Wykonaj te same dotyczące ścieżki biblioteki.  
  
#### <a name="windows-phone-81"></a>Windows Phone 8,1  
 Ponieważ zestaw Windows Phone 8.1 SDK nie zawiera nagłówka DXProgrammableCapture.h, musisz zdefiniować `IDXGraphicsAnalysis` interfejsu użytkownika, aby mogli używać `BeginCapture()` i `EndCapture()` metody. Zawierają inne nagłówki zgodnie z opisem w poprzedniej sekcji.  
  
###### <a name="to-define-the-idxgraphicsanalysis-interface"></a>Aby zdefiniować interfejsu IDXGraphicsAnalysis  
  
-   Zdefiniuj interfejs IDXGraphicsAnalysis w tym samym pliku, w którym są uwzględnione pliki nagłówków.  
  
    ```  
    interface DECLSPEC_UUID("9f251514-9d4d-4902-9d60-18988ab7d4b5") DECLSPEC_NOVTABLE  
    IDXGraphicsAnalysis : public IUnknown  
    {  
        STDMETHOD_(void, BeginCapture)() PURE;  
        STDMETHOD_(void, EndCapture)() PURE;  
    };  
    ```  
  
 Dla wygody można wykonać następujące kroki w nowym pliku nagłówka, a następnie dołącz ją w razie potrzeby w aplikacji.  
  
### <a name="getting-the-idxgraphicsanalysis-interface"></a>Uzyskiwanie interfejsu IDXGraphicsAnalysis  
 Przed rozpoczęciem przechwytywania informacji graficznych z DirectX 11.2, należy pobrać dxgi, za pomocą interfejsu debugowania.  
  
> [!IMPORTANT]
>  Używając przechwycenie programowe, można nadal uruchamiać aplikację pod nadzorem diagnostyki grafiki (Alt + F5 w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) lub w obszarze [przechwytywania narzędzie wiersza polecenia](command-line-capture-tool.md).  
  
##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Aby uzyskać interfejsu IDXGraphicsAnalysis  
  
-   Poniższy kod umożliwia podłączanie do interfejsu debugowania dxgi, za pomocą interfejsu IDXGraphicsAnalysis.  
  
    ```  
    IDXGraphicsAnalysis* pGraphicsAnalysis;  
    HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
    ```  
  
     Należy sprawdzić `HRESULT` zwrócony przez `DXGIGetDebugInterface1` zapewnienie uzyskać prawidłowy interfejs przed jego użyciem:  
  
    ```  
    if (FAILED(getAnalysis))  
    {  
        // Abort program or disable programmatic capture in your app.  
    }  
    ```  
  
    > [!NOTE]
    >  Jeśli `DXGIGetDebugInterface1` zwraca `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`), upewnij się, że aplikacja jest uruchomiona pod nadzorem diagnostyki grafiki (Alt + F5 w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).  
  
### <a name="capturing-graphics-information"></a>Przechwytywanie informacji graficznych  
 Teraz, gdy masz prawidłową `IDXGraphicsAnalysis` interfejsu, można użyć `BeginCapture` i `EndCapture` do przechwycenia informacji graficznych.  
  
##### <a name="to-capture-graphics-information"></a>Aby przechwytywanie informacji graficznych  
  
-   Aby uruchomić przechwytywanie informacji graficznych, użyj `BeginCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     Przechwytywanie rozpocznie się natychmiast po `BeginCapture` nazywa się; nie oczekuje na następną ramkę rozpocząć. Przechwyć zatrzymuje przedstawionej bieżącej ramki lub po wywołaniu `EndCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  
  
##  <a name="CaptureDX11_1"></a>Przechwycenie programowe w systemie Windows 8.0 i starszych wersji  
 Ta część przewodnika pokazuje przechwycenie programowe w aplikacji dla systemu Windows 8.0 i starszych wersji, które używają programu DirectX 11.1 interfejsu API, który używa metody przechwytywania starszej wersji. Aby uzyskać informacje o sposobie używania przechwycenie programowe w aplikacjach, które DirectX 11.2 w systemie Windows 8.1, zobacz [Programmatic przechwytywania w Windows 8.1](#CaptureDX11_2) we wcześniejszej części tego przewodnika.  
  
 Ta część zawiera następujące zadania:  
  
-   Trwa przygotowywanie komputera umożliwia przechwycenie programowe  
  
-   Przygotowywanie aplikacji do użycia przechwycenie programowe  
  
-   Konfigurowanie nazwy i lokalizacji pliku dziennika grafiki  
  
-   Przy użyciu `CaptureCurrentFrame` interfejsu API  
  
### <a name="preparing-your-computer-to-use-programmatic-capture"></a>Trwa przygotowywanie komputera umożliwia przechwycenie programowe  
 Przechwycenie programowe interfejs API korzysta z narzędzi Remote Tools for [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] umożliwiają korzystanie z funkcji przechwytywania. Komputer, na którym aplikacja będzie uruchamiana muszą być zainstalowane, nawet wtedy, gdy używasz przechwycenie programowe komputera lokalnego narzędzia zdalnego. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]nie musi być uruchomiona podczas wykonywania przechwycenie programowe na komputerze lokalnym.  
  
 Aby używać zdalnego przechwytywania interfejsów API w aplikacji, która jest uruchomiona na komputerze, najpierw należy zainstalować narzędzia zdalnej dla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] na tym komputerze. Różne wersje narzędzi remote Tools obsługują innych platform sprzętowych. Aby uzyskać informacje o sposobie instalowania narzędzi remote tools, zobacz [narzędzi zdalnych stronę pobierania](http://go.microsoft.com/fwlink/p/?LinkId=246691) w programie Microsoft pobiera witryny sieci Web.  
  
 Alternatywnie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instaluje składniki niezbędne do przeprowadzenia zdalnej rejestracji aplikacji 32-bitowych.  
  
> [!NOTE]
>  Ponieważ większość aplikacji klasycznych systemu Windows — w tym [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]— nie są obsługiwane w [!INCLUDE[win8](../includes/win8_md.md)] urządzeń ARM przy użyciu narzędzi Remote Tools for [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wraz z przechwycenie programowe interfejs API jest jedynym sposobem, aby przechwycić diagnostyki grafiki na urządzeniach ARM.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Przygotowywanie aplikacji do użycia przechwycenie programowe  
 Aby korzystać z narzędziami diagnostyki grafiki, należy najpierw przechwytywanie informacji graficznych, która opiera się na. Informacje można programowo Przechwyć, używając `CaptureCurrentFrame` interfejsu API.  
  
##### <a name="to-prepare-your-app-to-capture-graphics-information-programmatically"></a>Aby przygotować aplikację, aby programowe przechwytywanie informacji graficznych  
  
1.  Upewnij się, że `vsgcapture.h` nagłówek znajdzie się w kodzie źródłowym aplikacji. Można ją dołączyć tylko jednej lokalizacji — na przykład w pliku źródła kodu, w którym będzie wywoływać programowe Przechwytywanie interfejsu API — lub w pliku prekompilowanego nagłówka do wywołania interfejsu API z wielu plików kodu.  
  
2.  W kodzie źródłowym aplikacji, gdy mają być przechwytywane w pozostałej części bieżącej ramki, wywołania `g_pVsgDbg->CaptureCurrentFrame()`. Ta metoda nie przyjmuje żadnych parametrów i nie zwraca wartości.  
  
### <a name="configuring-the-name-and-location-of-the-graphics-log-file"></a>Konfigurowanie nazwy i lokalizacji pliku dziennika grafiki  
 Dziennik grafiki jest tworzony w lokalizacji, która jest definiowana za pomocą `DONT_SAVE_VSGLOG_TO_TEMP` i `VSG_DEFAULT_RUN_FILENAME` makra.  
  
##### <a name="to-configure-the-name-and-location-of-the-graphics-log-file"></a>Aby skonfigurować nazwę i lokalizację pliku dziennika grafiki  
  
-   Aby zapobiec dziennika grafiki zapisywany w katalogu tymczasowym, przed `#include <vsgcapture.h>` wiersz, dodaj to:  
  
    ```  
    #define DONT_SAVE_VSGLOG_TO_TEMP  
    ```  
  
     Można określić tę wartość, aby zapisać dziennika grafiki, lokalizacji, która jest względem katalogu roboczego, lub ścieżką bezwzględną Jeśli definicja `VSG_DEFAULT_RUN_FILENAME` jest ścieżką bezwzględną.  
  
-   Zapisz dziennik grafiki do innej lokalizacji lub nadać mu inną nazwę pliku, przed `#include <vsgcapture.h>` wiersz, dodaj to:  
  
    ```  
    #define VSG_DEFAULT_RUN_FILENAME <filename>  
    ```  
  
     Jeśli nie wykonasz tej czynności, nazwa pliku jest default.vsglog. Jeśli nie zostały zdefiniowane `DONT_SAVE_VSGLOG_TO_TEMP`, następnie lokalizację pliku względem katalogu tymczasowego; w przeciwnym razie jest powiązane z katalogiem roboczym lub w innej lokalizacji, jeśli określony bezwzględnej nazwy pliku.  
  
 Aby uzyskać [!INCLUDE[win8_appname_long](../includes/win8_appname_long_md.md)] aplikacji, lokalizację katalogu tymczasowego są specyficzne dla każdego użytkownika i aplikacji i zwykle znajduje się w lokalizacji takiej jak C:\users\\*username*\AppData\Local\Packages\\ *nazwy rodziny pakietów*\TempState\\. Dla aplikacji klasycznych, lokalizację katalogu tymczasowego jest przeznaczony dla każdego użytkownika i zazwyczaj znajduje się w lokalizacji takiej jak C:\Users\\*username*\AppData\Local\Temp\\.  
  
> [!NOTE]
>  Można zapisać w określonej lokalizacji, musi mieć uprawnienia do zapisu w tej lokalizacji; w przeciwnym razie wystąpi błąd. Należy pamiętać, że [!INCLUDE[win8_appname_long](../includes/win8_appname_long_md.md)] aplikacje są bardziej ograniczony w aplikacjach klasycznych, o których one można zapisać danych i mogą wymagać dodatkowej konfiguracji do zapisu w określonych lokalizacjach.  
  
### <a name="capturing-the-graphics-information"></a>Przechwytywanie informacji graficznych  
 Po przygotowywania aplikacji przechwycenie programowe i opcjonalnie skonfigurować lokalizację i nazwę grafiki pliku dziennika, kompilowania aplikacji i następnie uruchomić ani debugować go do przechwycenia danych; Nie uruchamiaj diagnostyki grafiki z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] korzystając programowe Przechwytywanie interfejsu API. Grafika dziennika są zapisywane w określonej lokalizacji. Jeśli chcesz zachować tę wersję dziennika, przenieś go do innej lokalizacji. w przeciwnym razie zostaną zastąpione, gdy ponownie uruchom aplikację.  
  
> [!TIP]
>  Można nadal przechwytywać informacji graficznych ręcznie podczas korzystania przechwycenie programowe — z aplikacją w fokus, wystarczy nacisnąć klawisz **Print Screen**. Ta metoda umożliwia przechwytywanie informacji graficznych dodatkowe, które nie są przechwytywane przez przechwycenie programowe interfejsu API.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku przedstawiono programowe przechwytywanie informacji graficznych. Jako kolejny krok Rozważ użycie tej opcji:  
  
-   Dowiedz się, jak do analizowania informacji graficznych przechwycone przy użyciu narzędzia diagnostyki grafiki. Zobacz [omówienie](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Przechwytywanie informacji graficznych](walkthrough-capturing-graphics-information.md)   
 [Przechwytywanie informacji graficznych](capturing-graphics-information.md)   
 [Narzędzie wiersza polecenia do przechwytywania](command-line-capture-tool.md)