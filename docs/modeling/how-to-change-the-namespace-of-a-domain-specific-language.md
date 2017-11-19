---
title: "Porady: Zmienianie Namespace języka specyficznego dla domeny | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: "19"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: b7419766b4c195c3bcef2aa45e886004a89fb5ec
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Porady: zmienianie przestrzeni nazw języka specyficznego dla domeny
Można zmienić przestrzeni nazw języka specyficznego dla domeny. Należy zmienić w **DSL Explorer**, we właściwościach projektu Dsl pakietu oraz informacje o zestawie.  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Aby zmienić przestrzeń nazw języka specyficznego dla domeny  
  
1.  W **DSL Explorer**, kliknij przycisk **Dsl** węzła.  
  
2.  W **właściwości** Zmień **Namespace** właściwości.  
  
3.  Zapisz rozwiązanie i przekształcenie szablonów.  
  
4.  Na **projektu** menu, kliknij przycisk **właściwości Dsl**.  
  
     Właściwości projektu są wyświetlane.  
  
5.  Kliknij przycisk **aplikacji** kartę.  
  
6.  Zmień **domyślny obszar nazw** właściwości na nową nazwę przestrzeni nazw.  
  
7.  Jeśli chcesz także zmienić nazwę zestawu, zmień **Nazwa zestawu.**  
  
8.  Jeśli zmienisz nazwę zestawu, otwórz DslPackage\Package.tt i zaktualizować ten wiersz:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Jeśli w języku dowolny kod niestandardowy, upewnij się zmienić odwołania do przestrzeni nazw i klasy w plikach kodu.  
  
10. Zresetuj Visual Studio eksperymentalne wystąpienie.  
  
    1.  Usuń **\Users\\***{nazwa}***\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2.  W systemie Windows **Start** menu, wybierz **wszystkie programy**, **zestawu SDK programu Microsoft Visual Studio 2010**, **narzędzia**, **resetowania Eksperymentalne wystąpienie**.  
  
11. Na **kompilacji** menu, wybierz **Kompiluj ponownie rozwiązanie**.  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)