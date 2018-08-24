---
title: Zagadnienia dotyczące zabezpieczeń internetowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, security
- security [Visual Studio], visualizers
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f041aa4506906291f429e8825ca42b7ea30f14c4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42690889"
---
# <a name="visualizer-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń internetowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [zagadnienia dotyczące zabezpieczeń internetowych](https://docs.microsoft.com/visualstudio/debugger/visualizer-security-considerations).  
  
Pisanie wizualizatora polega na potencjalne zagrożenia. Dla tych potencjalnych zagrożeń istnieje obecnie nie znane luki, ale deweloperów powinna wiedzieć o tym i podjąć odpowiednie środki ostrożności, zgodnie z opisem w tym miejscu, w celu ochrony przed programami wykorzystującymi luki w przyszłości.  
  
 Wizualizatory debugera wymagają większe uprawnienia niż jest to dozwolone przez aplikację do częściowego zaufania. Wizualizatory nie zostanie załadowany, gdy zostały zatrzymane w kod z częściowej relacji zaufania. Aby debugować za pomocą wizualizatora, należy uruchomić kod z pełnym zaufaniem.  
  
## <a name="possible-malicious-debuggee-component"></a>Możliwe złośliwego składnik obiekcie debugowanym  
 Wizualizatory składają się z co najmniej dwóch klas: na stronie debugera i jeden po stronie debugowanego obiektu. Wizualizatory są często wdrażana w oddzielne zestawy, umieść w katalogach specjalne, ale mogą również być załadowany z debugowanego obiektu. W takiej sytuacji debuger kodu poza obiekt debugowany i uruchamia go wewnątrz debugera z pełnym zaufaniem.  
  
 Uruchamianie kodu po stronie debugowanego obiektu z pełnym zaufaniem staje się problematyczne Jeśli obiekt debugowany nie jest w pełni zaufany. Jeśli wizualizatora próbuje załadować zestaw częściowej relacji zaufania z debugowanym obiekcie do debugera, Visual Studio przestanie obowiązywać wizualizatora.  
  
 Jednak nadal istnieje pomocnicza luk w zabezpieczeniach. Po stronie debugowanego obiektu można skojarzyć z boku debugera, który został załadowany z innego źródła (a nie obiekt debugowany). Po stronie debugowanego obiektu można powiedzieć, zaufanych stronie debugera do wykonania akcji w jej imieniu. Jeśli zaufany klasy po stronie debugera udostępnia mechanizm "Usuń ten plik", na przykład obiekt debugowany częściowego zaufania może wywołać ten mechanizm po użytkownik wywołuje jego wizualizatora.  
  
 Aby zmniejszyć tę lukę w zabezpieczeniach, należy zachować ostrożność, interfejsów udostępnianych przez usługi wizualizatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura wizualizatora](../debugger/visualizer-architecture.md)   
 [Porady: pisanie wizualizatora](../debugger/how-to-write-a-visualizer.md)   
 [Tworzenie niestandardowych Wizualizatorów](../debugger/create-custom-visualizers-of-data.md)   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)



