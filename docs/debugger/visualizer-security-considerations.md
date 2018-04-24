---
title: Zagadnienia dotyczące zabezpieczeń internetowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, security
- security [Visual Studio], visualizers
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 799cc8700c450fb2d8b81293bf410903e498e19c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="visualizer-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń internetowych
Pisanie wizualizatora polega na potencjalne zagrożenia. Nie znanego wykorzystać nie istnieje dla tych potencjalnych zagrożeń, ale deweloperów powinien mieć świadomość ich i podjąć odpowiednie środki ostrożności, zgodnie z opisem w tym miejscu, w celu ochrony przed lukami w przyszłości.  
  
 Wizualizatory debugera wymagają uprawnień większa, niż jest to dozwolone przez aplikację częściowej relacji zaufania. Wizualizatory nie zostanie załadowany, gdy zostały zatrzymane w kodzie z częściowa relacja zaufania. Aby debugować przy użyciu wizualizatora, należy uruchomić kod z pełnym zaufaniem.  
  
## <a name="possible-malicious-debuggee-component"></a>Możliwe złośliwego składnika obiektu debugowanego  
 Wizualizatory składają się z co najmniej dwie klasy: na stronie debugera i jeden po stronie debugowanego obiektu. Wizualizatory często są wdrażane w oddzielne zestawy umieścić w katalogach specjalne, ale mogą również być załadowany z obiektem debugowanym. W takim przypadku debuger kodu poza obiekt debugowany i uruchamia go wewnątrz debugera przy pełnym zaufaniu.  
  
 Uruchomienia kodu po stronie debugowanego obiektu z pełnym zaufaniem staje się powodować problemy podczas debugowany nie jest w pełni zaufany. Jeśli wizualizatora próbuje załadować częściowo zaufanego zestawu z obiektem debugowanym do debugera, Visual Studio spowoduje przerwanie wizualizatora.  
  
 Jednak nadal istnieje luka pomocniczych. Po stronie debugowanego obiektu można skojarzyć z strona debugera, która została załadowana z innego źródła (nie debugowany). Po stronie debugowanego obiektu następnie można określić, która zaufanych po stronie debugera do wykonania akcji w jego imieniu. Jeśli zaufane klasy po stronie debugera udostępnia mechanizm "Usuń ten plik", na przykład obiekt debugowany częściowego zaufania może wywołać mechanizmu gdy użytkownik wywoła jego wizualizatora.  
  
 Aby zmniejszyć tę lukę w zabezpieczeniach, należy zachować ostrożność, interfejsów udostępnianych przez użytkownika wizualizatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura wizualizatora](../debugger/visualizer-architecture.md)   
 [Porady: pisanie wizualizatora](../debugger/how-to-write-a-visualizer.md)   
 [Utwórz niestandardowe Wizualizatory](../debugger/create-custom-visualizers-of-data.md)   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)