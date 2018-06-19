---
title: Odinstalowywanie pakiet VSPackage z Instalatorem Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d8a62692003b26afcd5b7814bdc03320fa1c453a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31141099"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Odinstalowywanie pakiet VSPackage za pomocą Instalatora Windows
W większości przypadków Instalatora Windows można odinstalować VSPackage tylko przez "Cofanie" zastosowała do zainstalowania VSPackage. Akcje niestandardowe omówione w [polecenia czy musi być Uruchom po instalacji](../../extensibility/internals/commands-that-must-be-run-after-installation.md) musi być uruchamiane po odinstalowaniu również. Ponieważ wywołań devenv.exe występować bezpośrednio przed działania standardowe funkcję InstallFinalize dla instalacji i dezinstalacji, wpisy tabeli Akcja niestandardowa i InstallExecuteSequence obsługiwać obu przypadkach.  
  
> [!NOTE]
>  Uruchom `devenv /setup` po odinstalowaniu pakietu MSI.  
  
 Jako ogólną regułę Jeśli Dodaj niestandardowe akcje do pakietu Instalatora Windows, należy samodzielnie te czynności podczas dezinstalacji i wycofywania. Jeśli dodasz akcje niestandardowe, aby zarejestrować się samodzielnie VSPackage, na przykład musi dodać akcje niestandardowe wyrejestrować, zbyt.  
  
> [!NOTE]
>  Istnieje możliwość, aby użytkownik mógł zainstalować VSPackage, a następnie odinstaluj wersje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] z którego jest zintegrowany. Pomaga zagwarantować dezinstalacji programu pakiet VSPackage działa przez wyeliminowanie akcje niestandardowe, które uruchomić kod z zależnościami, w tym scenariuszu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Obsługa warunków uruchamiania na dezinstalacji.  
 Działania standardowe LaunchConditions odczytuje wiersze w tabeli LaunchCondition, aby wyświetlić błąd komunikaty, jeśli warunki nie są spełnione. Jak warunków uruchamiania są zazwyczaj używane do zapewnienia, że spełnione są wymagania systemowe, można zwykle pominąć warunków uruchamiania podczas odinstalowywania, dodając warunek, `NOT Installed`, aby wiersz LaunchConditions tabeli LaunchCondition.  
  
 Alternatywą jest dodanie `OR Installed` można uruchomić warunki, które nie są ważne podczas dezinstalacji. Która sprawia, że warunku będzie zawsze równa true podczas dezinstalacji i w związku z tym nie będzie wyświetlany komunikat o błędzie warunek uruchomienia.  
  
> [!NOTE]
>  `Installed` jest właściwością zestawów Instalatora Windows, gdy wykryje, że VSPackage został już zainstalowany w systemie.  
  
## <a name="see-also"></a>Zobacz też  
 [Instalator systemu Windows](http://msdn.microsoft.com/en-us/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md)