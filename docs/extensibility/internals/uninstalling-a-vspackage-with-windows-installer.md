---
title: Odinstalowywanie pakiet VSPackage z Instalatorem Windows | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b71c977fcc616c6d9cf30b78c9fd7610f11bcd4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
>  `Installed`jest właściwością zestawów Instalatora Windows, gdy wykryje, że VSPackage został już zainstalowany w systemie.  
  
## <a name="see-also"></a>Zobacz też  
 [Instalator systemu Windows](http://msdn.microsoft.com/en-us/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Wykrywanie wymagania systemowe](../../extensibility/internals/detecting-system-requirements.md)