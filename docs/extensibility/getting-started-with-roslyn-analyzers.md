---
title: "Wprowadzenie do korzystania z analizatorów Roslyn | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ec424f5e85f5bff9be5b276b3978b25dc3239fe5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-roslyn-analyzers"></a>Wprowadzenie do korzystania z analizatorów Roslyn
Z analizatorów kodu na żywo, na podstawie projektu w programie Visual Studio autorzy interfejsu API mogą być analizy kodu specyficznego dla domeny w ramach pakietów NuGet.  Ponieważ analizatory te są obsługiwane przez platformę .NET kompilatora (nazwę kodową "Roslyn"), jak po wpisaniu nawet po zakończeniu wiersza (nie więcej oczekiwanie, aby utworzyć swój kod, aby wykryć problemy) może powodować ostrzeżeń w kodzie.  Analizatory mogą również powierzchni poprawka automatyczne kodu za pomocą wiersza żarówki Visual Studio umożliwia czyszczenie kodu natychmiast  
  
## <a name="getting-started"></a>Wprowadzenie  
 [Analizatorów kodu na żywo Roslyn wprowadzenia i wskazówki](https://msdn.microsoft.com/en-us/magazine/dn879356.aspx)  
  
 [Dodanie kodu poprawki wskazówki: Podaj poprawki użytkowników dla analizatora problemów](https://msdn.microsoft.com/en-us/magazine/dn904670.aspx)  
  
 [Wprowadzenie oraz wskazówki dyskretne analizatora rzeczywistych](http://channel9.msdn.com/events/Build/2015/3-725)  
  
 [Rzeczywiste analizator Roslyn World](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , który można również obejrzeć jako [rozmowy](http://channel9.msdn.com/events/Build/2015/3-725)  
  
 [Kilka przykładów w witrynie github, podzielone na trzy rodzaje analizatorów](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)  
  
 [Wprowadzenie i samouczek analizatorów kilka rozmowy](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)  
  
## <a name="other-resources"></a>Inne zasoby  
 [Więcej dokumentów w witrynie github OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)  
  
 [Zasady programu FxCop realizowana za pomocą analizatorów Roslyn w witrynie github](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)