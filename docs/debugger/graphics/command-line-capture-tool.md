---
title: Narzędzie wiersza polecenia przechwytywania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f284fdbd4172c560c30aa3d7defb8a496e8e8e9d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="command-line-capture-tool"></a>Narzędzie wiersza polecenia przechwytywania
DXCap.exe to narzędzie wiersza polecenia do przechwytywania diagnostyki grafiki i odtwarzania. Obsługuje ona Direct3D 10 do Direct3D 12 na wszystkich poziomach funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```ms-dos  
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]  
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]  
DXCap.exe -p [filename] -screenshot [-frame frames]  
DXCap.exe -p [filename] -toXML [xml_filename]  
DXCap.exe -v [-file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]  
DXCap.exe -e [search_string]  
DXCap.exe -info  
```  
  
#### <a name="parameters"></a>Parametry  
 `-file``filename`  
 W trybie przechwytywania (`-c`), `filename` Określa nazwę pliku dziennika grafiki zapisaną informacji graficznych. Jeśli `filename` nie zostanie określony, informacji graficznych jest rejestrowany w pliku o nazwie `<appname>-<date>-<time>.vsglog` domyślnie.  
  
 W obszarze sprawdzania poprawności (-v) trybie `filename` Określa nazwę pliku dziennika grafiki do sprawdzenia poprawności. Jeśli `filename` nie zostanie określony, dziennik grafiki, który ostatniego sprawdzenia poprawności jest używane ponownie.  
  
 `-frame``frames`  
 W trybie przechwytywania `frames` określa ramek, które mają być przechwytywane. Pierwsza ramka jest 1. Można określić wiele ramek przy użyciu przecinków i zakresów. Na przykład jeśli `frames` jest `2, 5, 7-9, 15`, następnie ramki `2`, `5`, `7`, `8`, `9`, i `15` są przechwytywane.  

> [!TIP]
> Użyj `-frame` `manual` do określenia, że ramki zostanie ręcznie przechwycone przez naciśnięcie klawisza Print Screen. Po uruchomieniu aplikacji; można przechwycić ramki Aby zatrzymać przechwytywanie ramek, wróć do interfejsu wiersza polecenia i naciśnij klawisz enter.  
  
 `-period``periods`  
 W trybie przechwytywania `periods` określa zakres czasu, w sekundach, w których chcesz przechwytywać ramki. Można określić wiele okresów, przy użyciu przecinków i zakresów. Na przykład jeśli `periods` jest `2.1-5, 7.0-9.3`, a następnie ramek, które mają być renderowane między `2.1` i `5` sekund, a między`7` i `9.3` sekund są przechwytywane.  
  
 `-c` `app` [`args...`]  
 Przechwyć tryb. W trybie przechwytywania `app` Określa nazwę aplikacji, którą chcesz przechwytywanie informacji graficznych; `args...` określa dodatkowe parametry wiersza polecenia do danej aplikacji.  
  
 `-p` [`filename`]  
 Tryb odtwarzania (`-p`). W trybie odtwarzania `filename` Określa nazwę pliku dziennika grafiki, aby go odtworzyć. Jeśli `filename` nie zostanie określony, dziennik grafiki, który został ostatnio odtwarzane jest używane ponownie.  
  
 `-debug`  
 W trybie odtwarzania `-debug` Określa, że odtwarzania powinny być wykonywane z warstwą debugowania Direct3D włączone.  
  
 `-warp`  
 W trybie odtwarzania `-warp` Określa, że odtwarzania powinny być wykonywane przy użyciu renderowanie programowe WARP.  
  
 `-hw`  
 W trybie odtwarzania `-hw` Określa, że odtwarzania powinny być wykonywane przy użyciu sprzętu procesora GPU.  
  
 `-config`  
 W trybie odtwarzania `-config` Wyświetla informacje o maszynie użytej do przechwytywania grafiki pliku dziennika, jeśli te informacje został zapisany w dzienniku.  
  
 `-rawmode`  
 W trybie odtwarzania `-rawmode` Określa, że odtwarzania powinny być wykonywane bez modyfikacji zarejestrowane zdarzenia. W normalnych warunkach trybie odtwarzania wprowadzać drobne zmiany odtwarzania do uproszczenia, debugowanie i przyspieszenia odtwarzania. Na przykład może zasymulować dane wyjściowe łańcucha wymiany, a nie wykonywania poleceń łańcucha wymiany. Zazwyczaj nie jest to problem, ale może być konieczne odtwarzania w taki sposób, który jest bardziej dobrej wierze, aby zarejestrowane zdarzenia; na przykład służy tę opcję, aby przywrócić pełnego ekranu renderowania zachowanie aplikacji, która została przechwycona podczas pracy w trybie pełnoekranowym.  
  
 `-toXML` [`xml_filename`]  
 W trybie odtwarzania `xml_filename` Określa nazwę pliku, w którym zapisywana jest reprezentację XML odtwarzania. Jeśli `xml_filename` nie zostanie określony, reprezentacja w formacie XML są zapisywane w pliku o nazwie taki sam jak plik jest odtwarzany, ale podany `.xml` rozszerzenia.  
  
 `-v`  
 Tryb walidacji. W trybie sprawdzania poprawności ramki przechwycone są odtwarzane na sprzęt i WARP, a ich wyniki są porównywane przy użyciu funkcji porównanie obrazu. Ta funkcja umożliwia szybką identyfikację problemów sterowników, które wpływają na Twoje renderowania.  
  
 `-examine``events`  
 W obszarze tryb walidacji `events` określa zestaw zdarzeń grafiki, którego natychmiastowego wyniki są porównywane. Na przykład `-examine present,draw,copy,clear` ogranicza porównanie z tylko zdarzenia należące do tych kategorii.  
  
> [!TIP]
>  Firma Microsoft zaleca, począwszy od `-examine present,draw,copy,clear` ponieważ spowoduje to ujawnić większości problemów, ale trwać znacznie krócej niż szerszy zestaw zdarzeń. Jeśli to konieczne, można określić zestaw większy lub innych zdarzeń, aby sprawdzić te zdarzenia i ujawnić inne rodzaje problemów.  
  
 `-haltonfail`  
 W obszarze tryb walidacji `-haltonfail` zatrzymuje weryfikacji po wykryciu różnice między sprzętu i renderowania WARP. Sprawdzanie poprawności wznawia działanie po naciśnięciu klawisza.  
  
 `-exitonfail`  
 W obszarze tryb walidacji `-exitonfail` kończy działanie sprawdzania poprawności, natychmiast po wykryciu różnice między sprzętu i renderowania WARP. Gdy program kończy się w ten sposób, zwraca `0` środowiska; w przeciwnym razie zwraca `1`.  
  
 `-showprogress`  
 W obszarze tryb walidacji `-showprogress` Wyświetla informacje o postępie o sesji sprawdzania poprawności. WARP postęp jest wyświetlany po lewej stronie; sprzęt postęp jest wyświetlany po prawej stronie.  
  
 `-e``search_string`  
 Wylicza aplikacji platformy uniwersalnej systemu Windows, które są zainstalowane. Te informacje można użyć do wykonania wiersza polecenia przechwytywane z aplikacjami platformy uniwersalnej systemu Windows.  
  
 `-info`  
 Wyświetla informacje dotyczące bibliotek DLL maszyny i przechwytywania.  
  
## <a name="remarks"></a>Uwagi  
 DXCap.exe działa w trzech trybów:  
  
 Przechwyć w trybie (-c)  
 Przechwytywanie informacji graficznych w uruchomionej aplikacji i zarejestruj go w pliku dziennika grafiki. Możliwości przechwytywania i format pliku są identyczne z programu Visual Studio.  
  
 Tryb odtwarzania (-p)  
 Odtwarzanie zdarzeń grafiki przechwyconych wcześniej z istniejącego pliku dziennika grafiki. Domyślnie odtwarzania występuje w oknie, nawet wtedy, gdy dziennika grafiki plików przechwyconej z aplikacji pełny ekran. Odtwarzanie występuje w trybie pełnoekranowym tylko podczas logowania grafiki plików przechwyconej z aplikacji fullscreen i `-rawmode` jest określona.  
  
 Tryb walidacji (`-v`)  
 Weryfikuje sposób renderowania odtwarzanie do tyłu ramki przechwycone na sprzęt i WARP, a następnie porównanie ich wyników za pomocą funkcji porównanie obrazu. Ta funkcja umożliwia szybką identyfikację problemów sterowników, które wpływają na Twoje renderowania.  
  
 Oprócz tych trybów dxcap.exe wykonuje dwie funkcje, które nie wykonuj przechwytywania lub odtwarzania informacji graficznych.  
  
 Funkcja wyliczania (`-e`)  
 Wyświetla szczegółowe informacje o aplikacji platformy uniwersalnej systemu Windows, które są zainstalowane na tym komputerze. Te informacje obejmują nazwę pakietu i identyfikator aplikacji, które identyfikują plik wykonywalny w aplikacji platformy uniwersalnej systemu Windows. Aby przechwytywanie informacji graficznych z aplikacji ze sklepu windows przy użyciu DXCap.exe, należy użyć nazwy pakietu i appid zamiast nazwy pliku wykonywalnego używanego podczas przechwytywania aplikacji komputerowej.  
  
 Informacje o funkcji)`-info)`  
 Przedstawia szczegółowe informacje dotyczące bibliotek DLL maszyny i przechwytywania.  
  
## <a name="examples"></a>Przykłady  
  
### <a name="capture-graphics-information-from-a-desktop-app"></a>Przechwytywanie informacji graficznych z aplikacji klasycznych  
 Użyj `-c` do określenia aplikacji, z którego mają być przechwytywane informacji graficznych.  
  
```ms-dos  
DXCap.exe -c BasicHLSL11.exe  
```  
  
 Domyślnie informacji graficznych jest rejestrowany w pliku o nazwie `<appname>-<date>-<time>.vsglog`. Użyj `-file` Aby określić inny plik do rejestrowania się.  
  
```ms-dos  
DXCap.exe -file regression_test_12.vsglog -c BasicHLSL11.exe  
```  
  
 Określ dodatkowe parametry wiersza polecenia do aplikacji, która jest przechwytywanie od, umieszczając je po filename aplikacji.  
  
```ms-dos  
DXCap.exe -c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"  
```  
  
 W powyższym przykładzie polecenia przechwytuje informacje dotyczące grafiki z tej wersji programu Internet Explorer podczas wyświetlania strony sieci Web w www.fishgl.com używający interfejsu API WebGL do renderowania zawartości 3-w lokalizacji.  
  
> [!NOTE]
>  Ponieważ argumenty wiersza polecenia, które pojawią się po aplikacji są przekazywane do niego, należy określić argumenty przeznaczonych do DXCap.exe przed użyciem `-c` opcji.  
  
### <a name="capture-graphics-information-from-a-uwp-app"></a>Przechwytywanie informacji graficznych z aplikacji platformy uniwersalnej systemu Windows.  
 Można przechwycić informacji graficznych z aplikacji platformy uniwersalnej systemu Windows.  
  
```ms-dos  
DXCap.exe -c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps  
```  
  
 Przechwytywania z aplikacji platformy uniwersalnej systemu Windows za pomocą DXCap.exe jest podobny do sposobu używania go do przechwycenia z aplikacji klasycznej systemu Windows, ale zamiast tego zidentyfikowania aplikacji komputerowej nazwy, zidentyfikuj aplikacji platformy uniwersalnej systemu Windows, jego nazwa pakietu i nazwę lub identyfikator wewnątrz pliku wykonywalnego, który pakietu, który ma być  Przechwyć z. Aby ułatwić dowiedzieć się, jak zidentyfikować aplikacji platformy uniwersalnej systemu Windows, które są zainstalowane na tym komputerze, należy użyć `-e` opcji DXCap.exe wyliczyć je:  
  
```ms-dos  
DXCap.exe -e  
```  
  
 Można podać ciąg opcjonalne wyszukiwania ułatwiają znajdowanie aplikacji, którego szukasz. Jeśli podany ciąg wyszukiwania DXCap.exe wylicza aplikacji platformy uniwersalnej systemu Windows, którego nazwa pakietu, nazwa aplikacji lub identyfikatorów aplikacji odpowiada ciąg wyszukiwania. Wyszukiwanie jest rozróżniana wielkość liter.  
  
```ms-dos  
DXCap.exe -e map  
```  
  
 Polecenie powyżej wylicza aplikacji platformy uniwersalnej systemu Windows, które odpowiada "map"; Poniżej przedstawiono dane wyjściowe:  
  
 **Pakiet "Microsoft.BingMaps":**  
 **InstallDirectory : C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **FullName         : Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **UserSID: S-1-5-21-2127521184-1604012920-1887927527-5603533**  
 **Nazwa: Microsoft.BingMaps**  
 **Wydawca: CN = Microsoft Corporation, O = Microsoft Corporation, L = Redmond, S Waszyngton, C = = US**  
 **Wersja: 2.1.2914.1734**  
 **Możliwych do uruchomienia aplikacji:**  
 **Identyfikator: AppexMaps**  
 **Exe  : C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe**  
 **IsWWA: nie**  
 ** AppSpec (do uruchamiania): **DXCap.exe - c Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps*** ostatni wiersz danych wyjściowych dla każdej aplikacji wyliczany wyświetla polecenie umożliwia przechwytywanie informacji graficznych z niego.  
  
### <a name="capture-specific-frames-or-frames-between-specific-times"></a>Przechwycić ramki określonych lub ramki między określonym czasie.  
 Użyj `-frame` określić ramek, które mają być przechwytywane przy użyciu przecinków i zakresów:  
  
```ms-dos  
DXCap.exe -frame 2,5,7-9,15 -c SimpleBezier11.exe  
```  
  
 Możesz też użyć `-period` do określenia zestawu przedziałów czasu, w którym mają być przechwytywane ramki. Podane przedziałów czasu w sekundach i można określić wiele zakresów:  
  
```ms-dos  
DXCap.exe -period 2.1-5, 7.0-9.3 -c SimpleBezier11.exe  
```  
  
### <a name="capture-frames-interactively"></a>Interaktywnie przechwycić ramki.  
 Użyj `-manual` Aby przechwycić ramki interaktywnie. Naciśnij klawisz Enter, aby rozpocząć przechwytywanie, a następnie naciśnij klawisz Enter, aby zatrzymać.  
  
```ms-dos  
DXCap.exe -manual -c SimpleBezier11.exe  
```  
  
### <a name="play-back-a-graphics-log-file"></a>Odtwarzanie plików dziennika grafiki  
 Użyj `-p` do odtwarzania pliku dziennika grafiki przechwyconych wcześniej.  
  
```ms-dos  
DXCap.exe -p regression_test_12.vsglog  
```  
  
 Opuść nazwę pliku, aby odtworzyć dziennik grafiki przechwyconej ostatnio.  
  
```ms-dos  
DXCap.exe -p  
```  
  
### <a name="play-back-in-raw-mode"></a>Odtwarzanie w trybie raw  
 Użyj `-rawmode` odtwarzać przechwyconych poleceń, dokładnie tak, jak ich wystąpienia. W obszarze normalne odtwarzanie niektórych poleceń są emulowane, na przykład plik dziennika grafiki przechwytywane z pełnego ekranu aplikacji zostaną odtworzone w oknie; włączono obsługę trybu raw ten sam plik będzie podejmować próby odtwarzanie na pełnym ekranie.  
  
```ms-dos  
DXCap.exe -p regression_test_12.vsglog -rawmode  
```  
  
### <a name="play-back-using-warp-or-a-hardware-device"></a>Odtwórz przy użyciu WARP lub urządzenia sprzętowego  
 Można wymusić odtwarzania obu plik dziennika grafiki przechwycone na urządzenie, aby użyć WARP lub wymusić odtwarzania dziennika przechwycone na WARP do użycia z urządzeniem sprzętowym. Użyj `-warp` prowadzonych ponownie przy użyciu WARP.  
  
```ms-dos  
DXCap.exe -p regression_test_12.vsglog -warp  
```  
  
 Użyj `-hw` prowadzonych ponownie przy użyciu sprzętu.  
  
```ms-dos  
DXCap.exe -p regression_test_12.vsglog -hw  
```  
  
### <a name="validate-a-graphics-log-file-against-warp"></a>Sprawdzanie poprawności względem WARP pliku dziennika grafiki  
 W trybie weryfikacji pliku dziennika grafiki odtwarzania na sprzęt i WARP, a ich wyniki są porównywane. Może to pomóc w identyfikacji błędów renderowania, które są spowodowane przez sterownik. -V umożliwia sprawdzanie poprawności poprawne zachowanie grafiki sprzętu przed WARP.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog  
```  
  
 Aby zmniejszyć ilość porównań, można określić podzestaw poleceń porównać sprawdzanie poprawności i innych poleceń zostaną zignorowane. Użyj - Sprawdź Aby określić polecenie, którego chcesz porównać wyniki.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog -examine present,draw,copy,clear  
```  
  
### <a name="convert-a-graphics-log-file-to-pngs"></a>Konwertowanie pliku dziennika grafiki PNG  
 Aby wyświetlić lub analizy ramek z plikiem dziennika grafiki, DXCap.exe zapisać ramki przechwycone jako .png pliki obrazów (Portable Network Graphics). Użyj `-screenshot` się w trybie odtwarzania, aby dane wyjściowe przechwycić ramki jako pliki PNG.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot  
```  
  
 Użyj `-frame` z `-screenshot` określa ramki, które ma zostać wyprowadzony.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot -frame 5, 7-9  
```  
  
### <a name="convert-a-graphics-log-file-to-xml"></a>Konwertowanie pliku dziennika grafiki XML  
 Przetwarzanie i analizowanie dzienników grafiki przy użyciu znanych narzędzi, takich jak FindStr lub XSLT, DXCap.exe można przekonwertować pliku dziennika grafiki do pliku XML. Użyj `-toXML` w trybie odtwarzania, aby przekonwertować dziennika XML zamiast jego odtwarzanie kopii.  
  
```ms-dos  
DXCap.exe -p regression_test_12.vsglog -toXML  
```  
  
 Domyślnie dane wyjściowe XML są zapisywane w pliku z taką samą nazwę jak dziennika grafiki, ale który ma rozszerzenie .xml. W powyższym przykładzie będzie miała nazwę pliku XML **regression_test_12.xml**. Aby podać inną nazwę pliku XML, określ je po `-toXML`.  
  
```ms-dos  
DXCap.exe -p regression_test_12.vsglog -toXML temp.xml  
```  
  
 Wynikowy plik będzie zawierał XML, która wygląda podobnie do poniższego:  
  
```xml  
<Moment value="67"/>  
<Method name="CreateDXGIFactory1" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />  
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />  
</Method>  
  
<Moment value="167"/>  
<Method name="D3D11CreateDevice" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />  
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />  
    <Parameter name="Software" type="HMODULE" value="pointer" />  
    <Parameter name="Flags" type="UINT" value="0" />  
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >  
        <Element value="D3D_FEATURE_LEVEL_11_0" />  
    </Parameter>  
    <Parameter name="FeatureLevels" type="UINT" value="1" />  
    <Parameter name="SDKVersion" type="UINT" value="7" />  
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />  
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />  
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />  
</Method>  
```  
  
## <a name="requirements"></a>Wymagania