---
title: "Zbieranie danych o interakcji między warstwy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
ms.assetid: 47a944c2-3098-497c-8fc7-e1f43d750bbc
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c12d279541e60353a9e6e4354a16870713498b66
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="collecting-tier-interaction-data"></a>Zbieranie danych o interakcji między warstwami
Profilowanie interakcji między warstwami udostępnia dodatkowe informacje o czas wykonywania funkcji aplikacji wielowarstwowych, które komunikują się z bazami danych za pośrednictwem usług ADO.NET. Dane są zbierane tylko dla wywołań synchronicznych funkcji.  
  
 **Wersje Visual Studio**  
  
 Można zbierać dane profilowania interakcji warstwy przy użyciu programu Visual Studio Ultimate, Visual Studio Premium lub Visual Studio Professional. Jednak tylko w ostatecznej wersji programu VS i VS Premium można wyświetlić danych profilowania interakcji warstwy.  
  
 **Windows 8 i Windows Server 2012**  
  
 Aby zbierać dane interakcji warstwy aplikacji klasycznych systemu Windows 8 i aplikacji systemu Windows Server 2012, należy użyć metody instrumentacji. Nie można zebrać danych o interakcji między warstwy dla aplikacji platformy uniwersalnej systemu Windows. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Warstwa danych o interakcji między mogą obejmować wszystkie metody profilowania w innej wersji systemu Windows.  
  
 **Kreator wydajności**  
  
 Z powodu błędu w Kreatorze wydajności należy dodać opcję zbierania danych interakcji warstwy do uruchomienia profilowania w Eksploratorze wydajności. Należy również dodać projekt, plik wykonywalny lub witryny sieci Web do węzła docelowego Eksplorator wydajności.  
  
### <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Aby dodać warstwę danych o interakcji między do profilowania uruchamiania za pomocą stron właściwości sesji wydajności  
  
1.  W Eksploratorze wydajności wybierz **właściwości** z menu kontekstowego.  
  
2.  Wybierz **interakcje warstw** strony, a następnie sprawdź **Włącz profilowanie interakcji między warstwami** pole wyboru.  
  
3.  W Eksploratorze wydajności wybierz **cele** węzeł, a następnie określ projekt, plik wykonywalny lub witryny sieci web, który ma zostać profilu.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok interakcji między warstwami](../profiling/tier-interactions-view.md)