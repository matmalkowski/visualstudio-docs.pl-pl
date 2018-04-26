---
title: Zastąpienia menedżera zawartości pomocy
ms.date: 11/01/2017
ms.prod: visual-studio-dev15
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0610178a6249d262169abbe32f3f6a93cdd0e935
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="help-content-manager-overrides"></a>Zastąpienia menedżera zawartości pomocy

Można zmienić domyślne zachowanie związane z pomocy funkcji w programie Visual Studio IDE i podglądu pomocy. Niektóre opcje są określone przez utworzenie [.pkgdef](https://blogs.msdn.microsoft.com/visualstudio/2009/12/18/whats-a-pkgdef-and-why/) pliku można ustawić różne wartości klucza rejestru. Inne są ustawiane bezpośrednio w rejestrze.

## <a name="how-to-control-help-viewer-behavior-by-using-a-pkgdef-file"></a>Sposób kontrolowania zachowania Podgląd pomocy za pomocą pliku .pkgdef

1. Utwórz *.pkgdef* pliku z pierwszego wiersza jako `[$RootKey$\Help]`.

2. Dodaj wybrane lub wszystkie wartości klucza rejestru opisanego w poniższej tabeli w osobnych wierszach, na przykład `“UseOnlineHelp”=dword:00000001`.

3. Skopiuj plik do *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\\< edition\>\Common7\IDE\CommonExtensions*.

4. Uruchom `devenv /updateconfiguration` w wierszu polecenia dewelopera.

### <a name="registry-key-values"></a>Wartości klucza rejestru

|Wartość klucza rejestru|Typ|Dane|Opis|
|------------------|----|----|-----------|
|NewContentAndUpdateService|string|\<adres HTTP URL punktu końcowego usługi\>|Zdefiniuj unikatowe punktu końcowego|
|UseOnlineHelp|DWORD|`0` Aby określić lokalnej pomocy, `1` do określenia pomocy online|Zdefiniuj domyślny pomocy online lub offline|
|OnlineBaseUrl|string|\<adres HTTP URL punktu końcowego usługi\>|Zdefiniuj unikatowe końcowy F1|
|OnlineHelpPreferenceDisabled|DWORD|`0` Aby włączyć lub `1` można wyłączyć opcji preferencji pomocy online|Wyłączanie opcji preferencji pomocy online|
|DisableManageContent|DWORD|`0` Aby włączyć lub `1` wyłączyć **zarządzania zawartością** kartę w Podglądzie pomocy|Wyłącz **zarządzania zawartością** kartę|
|DisableFirstRunHelpSelection|DWORD|`0` Aby włączyć lub `1` można wyłączyć funkcji pomocy, które są skonfigurowane po raz pierwszy uruchamia program Visual Studio|Wyłącz instalacji zawartości podczas pierwszego uruchomienia programu Visual Studio|

### <a name="example-pkgdef-file-contents"></a>Zawartość pliku .pkgdef przykład

```
[$RootKey$\Help]
“NewContentAndUpdateService”=”https://some.service.endpoint”
“UseOnlineHelp”=dword:00000001
“OnlineBaseUrl”=”https://some.service.endpoint”
“OnlineHelpPreferenceDisabled”=dword:00000000
“DisableManageContent”=dword:00000000
“DisableFirstRunHelpSelection”=dword:00000001
```

## <a name="use-registry-editor-to-change-help-viewer-behavior"></a>Użyj Edytora rejestru, aby zmienić zachowanie podglądu pomocy

Następujące dwa można kontrolować przez ustawienie wartości klucza rejestru w Edytorze rejestru.

|Zadanie|Klucz rejestru|Wartość|Dane|
|----------|-----|------|----|
|Zastąpienie priorytet zadania usługi BITS|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (na machine)\Microsoft\Help\v2.3 64-bitowych|BITSPriority|**pierwszego planu**, **wysokiej**, **normalne**, lub **niski**|
|Wskaż magazynu zawartości lokalnej w udziale sieciowym|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15|LocationPath|"*ContentStoreNetworkShare*"|

## <a name="see-also"></a>Zobacz także

- [Przewodnik administratora podglądu pomocy](../ide/help-viewer-administrator-guide.md)
- [Argumenty wiersza polecenia do menedżera zawartości pomocy](../ide/command-line-arguments-for-the-help-content-manager.md)
- [Podgląd Pomocy firmy Microsoft](../ide/microsoft-help-viewer.md)
- [Modyfikowanie przy użyciu pliku .pkgdef programu isolated shell](../extensibility/shell/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)