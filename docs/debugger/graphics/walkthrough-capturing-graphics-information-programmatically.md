---
title: 'Wskazówki: Programowe przechwytywanie informacji graficznych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a2caae8a3ef2a6342cf98094994d5ebccbe3275
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Wskazówki: programowe przechwytywanie informacji graficznych
Można użyć [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagnostyki grafiki do programowe przechwytywanie informacji graficznych z aplikacji Direct3D.  
  
 Przechwycenie programowe jest przydatne w scenariuszach, takich jak:  
  
-   Po swapchain istnieje, np. podczas renderowania jej tekstury nie korzysta z aplikacji grafiki programowo rozpocząć przechwytywania.  
  
-   Po aplikacji nie renderowania, np. gdy DirectCompute jest używane do obliczeń programistycznie rozpocząć przechwytywania.  
  
-   Wywołanie `CaptureCurrentFrame`Jeżeli problem z renderowaniem jest trudne do przewidywania i przechwytywania w testów ręcznych, ale można przewidzieć programowo przy użyciu informacji o stanie aplikacji w czasie wykonywania.  
  
##  <a name="CaptureDX11_2"></a> Przechwycenie programowe w systemie Windows 10  
 Ta część przewodnika pokazuje przechwycenie programowe w aplikacji, które używają interfejsu API programu DirectX 11.2 w systemie Windows 10, które używa metody przechwytywania niezawodny.
  
 W tej sekcji przedstawiono sposób wykonywania tych zadań:  
  
-   Przygotowywanie aplikacji do użycia przechwycenie programowe  
  
-   Uzyskiwanie interfejsu IDXGraphicsAnalysis  
  
-   Przechwytywanie informacji graficznych  
  
> [!NOTE]
>  Poprzednich implementacjach przechwycenie programowe zależał od Remote Tools for Visual Studio dla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] umożliwiają korzystanie z funkcji przechwytywania.
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Przygotowywanie aplikacji do użycia przechwycenie programowe  
 Aby użyć przechwycenie programowe w aplikacji, musi on zawierać niezbędne nagłówki. Te nagłówki są częścią zestawu Windows 10 SDK.  
  
##### <a name="to-include-programmatic-capture-headers"></a>Aby uwzględnić nagłówki przechwycenie programowe  
  
-   Zawiera tych nagłówków w pliku źródłowym, w którym zostaną zdefiniowane interfejsu IDXGraphicsAnalysis:  
  
    ```  
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    >  Nie dołączaj nagłówka vsgcapture.h—which obsługuje programowe Przechwytywanie plików w systemie Windows 8.0 i wcześniej — w celu wykonania przechwycenie programowe w aplikacjach systemu Windows 10. Ten nagłówek jest niezgodna z DirectX 11.2. Jeśli ten plik będzie po nagłówek d3d11_2.h jest dołączony, kompilator generuje ostrzeżenie. Jeśli vsgcapture.h znajduje się przed d3d11_2.h, aplikacja nie zostanie uruchomiona.  
  
    > [!NOTE]
    >  Jeśli 2010 czerwca DirectX SDK jest zainstalowany na tym komputerze i zawiera ścieżkę do załączenia projektu `%DXSDK_DIR%includex86`, przenieś go do końca ścieżki include. Wykonaj te same dotyczące ścieżki biblioteki.  
  
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
  
     Należy sprawdzić `HRESULT` zwrócony przez [DXGIGetDebugInterface1](https://msdn.microsoft.com/library/windows/desktop/dn457937(v=vs.85).aspx) zapewnienie uzyskać prawidłowy interfejs przed jego użyciem:  
  
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
  
- Aby uruchomić przechwytywanie informacji graficznych, użyj `BeginCapture`:  
  
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

- Po wywołaniu `EndCapture`, zwolnij obiekt grafiki. 
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku przedstawiono programowe przechwytywanie informacji graficznych. Jako kolejny krok Rozważ użycie tej opcji:  
  
-   Dowiedz się, jak do analizowania informacji graficznych przechwycone przy użyciu narzędzia diagnostyki grafiki. Zobacz [omówienie](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Przechwytywanie informacji graficznych](walkthrough-capturing-graphics-information.md)   
 [Przechwytywanie informacji graficznych](capturing-graphics-information.md)   
 [Narzędzie wiersza polecenia do przechwytywania](command-line-capture-tool.md)