---
title: 'Porady: Dodawanie zależności do pakietu VSIX | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0704a72ba70e2a00baab99d327702ec6c08f1775
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133225"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Porady: Dodawanie zależności do pakietu VSIX

Można skonfigurować wdrożenie pakietu VSIX, która instaluje wszystkie zależności, które nie są już istnieje na komputerze docelowym. W tym celu należy uwzględnić zależności pliku VSIX do pliku source.extension.vsixmanifest.

## <a name="to-add-a-dependency"></a>Aby dodać zależność

1. Otwórz plik Source.Extension.vsixmanifest,a w **projekt** widoku. Przejdź do **zależności** i kliknij polecenie **nowy**.

2. Aby dodać zainstalowanego rozszerzenia: w **Dodawanie nowych zależności** okno dialogowe, wybierz opcję **zainstalowane rozszerzenie** , a następnie w **nazwa**, zaznacz rozszerzenie na liście.

3. Aby dodać inny VSIX, który nie jest zainstalowany:: w **Dodawanie nowych zależności** okno dialogowe, wybierz opcję **pliku w systemie plików** , a następnie użyj **Przeglądaj** przycisk, aby wybrać pliku VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Wymaga określonej wersji programu Visual Studio

Jeśli rozszerzenie wymaga określonej wersji programu Visual Studio 2017, na przykład zależy od funkcji wydane w ramach 15 ustęp 3, można określić numer kompilacji w Twojej VSIX **InstallationTarget**. Na przykład wersji 15 ustęp 3 ma numer kompilacji programu "15.0.26730.3". Widać mapowania wydań numery kompilacji [tutaj](../install/visual-studio-build-numbers-and-release-dates.md). Należy pamiętać, że za pomocą numeru wersji 15 ustęp "3" może nie działać poprawnie.

Jeśli rozszerzenie wymaga 15 ustęp 3 lub nowszym, czy zadeklarować **wersji InstallationTarget** jako [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller wykryje wcześniejszych wersji programu Visual Studio i poinformować użytkownika, że późniejszą aktualizację jest wymagana.


## <a name="see-also"></a>Zobacz też

 [Odwołanie do schematu 1.0 rozszerzenia VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b) [anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md) [przygotowywania rozszerzeń dla wdrożenia Instalatora Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)