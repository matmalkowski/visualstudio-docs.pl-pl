---
title: 'Porady: Zmienianie Namespace języka specyficznego dla domeny | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1407b0ca77ea6f19bc6f6f165d5524c305b69d0f
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43774721"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Porady: zmienianie przestrzeni nazw języka specyficznego dla domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: Zmienianie Namespace języka specyficznego dla domeny](https://docs.microsoft.com/visualstudio/modeling/how-to-change-the-namespace-of-a-domain-specific-language).  
  
Można zmienić przestrzeni nazw języka specyficznego dla domeny. Należy wprowadzić zmianę w **Eksplorator DSL**, we właściwościach projektu Dsl pakietu oraz informacje o zestawie.  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Aby zmienić przestrzeni nazw języka specyficznego dla domeny  
  
1.  W **Eksplorator DSL**, kliknij przycisk **Dsl** węzła.  
  
2.  W **właściwości** oknie zmiany **Namespace** właściwości.  
  
3.  Zapisywanie rozwiązania i przekształcania szablonów.  
  
4.  Na **projektu** menu, kliknij przycisk **właściwości Dsl**.  
  
     Właściwości projektu są wyświetlane.  
  
5.  Kliknij przycisk **aplikacji** kartę.  
  
6.  Zmiana **domyślny obszar nazw** właściwości na nową nazwę przestrzeni nazw.  
  
7.  Jeśli chcesz także zmienić nazwę zestawu, zmień **właściwości nazwy zestawu.**  
  
8.  Jeśli zmieniono nazwę zestawu, otwórz DslPackage\Package.tt i zaktualizować ten wiersz:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Jeśli napisano kodu niestandardowego, upewnij się zmienić odwołania do przestrzeni nazw i klasy w plikach kodu.  
  
10. Zresetuj wystąpienie eksperymentalne programu Visual Studio.  
  
    1.  Usuń **\Users\\**_{name}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2.  Na Windows **Start** menu, wybierz **wszystkie programy**, **Microsoft Visual Studio 2010 SDK**, **narzędzia**, **resetowania Wystąpienie eksperymentalne**.  
  
11. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzi języka specyficznego dla domeny](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



