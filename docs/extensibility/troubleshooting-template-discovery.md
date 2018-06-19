---
title: Rozwiązywanie problemów z szablonu odnajdywania w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d183fd664258fbb7dbcf27c913c56c6f6160e6c4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136731"
---
# <a name="troubleshooting-template-installation"></a>Rozwiązywanie problemów z instalacją szablonu

Jeśli wystąpiły problemy wdrażanie szablonów projektu lub elementu, można włączyć rejestrowania diagnostycznego.

1. Tworzenie pliku pkgdef w folderze Common7\IDE\CommonExtensions instalacji (np. C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) z następującą zawartość:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. Otwórz wiersz "polecenie dewelopera" instalacji przez wyszukiwanie w wyszukiwania systemu Windows i uruchom `devenv /updateConfiguration`.

1. Uruchom program Visual Studio, a następnie uruchom okna dialogowe nowego projektu i nowy element zainicjować obu drzewach szablonu. Zostanie wyświetlony w dzienniku szablonu **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid identyfikatorowi Instalacja wystąpienia programu Visual Studio). Inicjowanie drzewa każdego szablonu dołącza wpisy w tym dzienniku.

Plik dziennika zawiera następujące kolumny:

- **FullPathToTemplate**, która zawiera następujące wartości:

    - 1 w przypadku wdrażania dla manifest

    - 0 dla wdrożenia opartego na dysku

- **TemplateFileName**

- Inne właściwości szablonu

> [!NOTE]
> Aby wyłączyć rejestrowanie, Usuń pliku pkgdef lub zmień wartość `EnableTemplateDiscoveryLog` do `dword:00000000`, a następnie uruchom `devenv /updateConfiguration` ponownie.

## <a name="see-also"></a>Zobacz także

[Tworzenie niestandardowych szablonów projektów i elementów](creating-custom-project-and-item-templates.md)