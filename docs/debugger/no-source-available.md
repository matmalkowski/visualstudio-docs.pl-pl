---
title: "Jest dostępne żadne źródło | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a11770bc54a7b96aa918b73b34e0028731bf0f9c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="no-source-available"></a>Nie jest dostępne żadne źródło
Projekt nie zawiera kodu źródłowego dla kodu, który chcesz wyświetlić. Najczęstszą przyczyną jest dwukrotnie moduł, który nie ma kodu źródłowego w **okna stosu wywołań** lub **okno wątków**. Można kontynuować debugowania, ale nie można użyć okna źródła można ustawić punktów przerwania i wykonywać inne akcje w tej lokalizacji. Jeśli trzeba ustawić punkt przerwania, użyj **dezasemblacja, okno** zamiast tego.  
  
 Na stronach właściwości rozwiązania można zmienić katalogi, w której debuger wyszukuje pliki źródłowe i poinformuj debugera do ignorowania plików wybranego źródła. Zobacz [debugowania źródła plików, typowe właściwości rozwiązania właściwości strony — okno dialogowe](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Przejdź do kodu źródłowego**  
 Kliknij to łącze, aby otworzyć okno dialogowe, którego można przeglądać można znaleźć kodu źródłowego.  
  
 **Pokaż Dezasemblację**  
 Uruchamia **dezasemblacja, okno**.  
  
 **Zawsze pokazuj dezasemblację dla brakujących plików źródłowych**  
 Wybierz tę opcję, aby wyświetlić **dezasemblacja, okno** automatycznie Jeśli żadne źródło nie jest dostępny. To ustawienie można zmienić w **opcje** okno dialogowe **debugowanie** kategorii, **ogólne** strony, zaznaczając lub usuwając **Pokaż dezasemblację, jeśli źródło nie jest dostępne**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie źródła plików, typowe właściwości rozwiązania właściwości strony — okno dialogowe](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (rozszerzenie do debugowania SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)