---
title: Strona zdarzenia kompilacji, Projektant projektu (C#) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c701adc4da2f59505699a02f1b4ccc304841f3ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="build-events-page-project-designer-c"></a>Strona Zdarzenia kompilacji, Projektant projektu (C#)
Użyj **zdarzeń kompilacji** strony **projektanta projektu** do określenia instrukcji konfiguracji kompilacji. Można również określić warunki, w których są uruchamiane wszystkie zdarzenia postkompilacyjnego. Aby uzyskać więcej informacji, zobacz [porady: Określanie zdarzeń kompilacji (C#)](../../ide/how-to-specify-build-events-csharp.md)i [porady: Określ kompilacji zdarzenia (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Konfiguracja**  
 Ten formant nie jest możliwa na tej stronie. Opis tego formantu, zobacz [strona kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Platformy**  
 Ten formant nie jest możliwa na tej stronie. Opis tego formantu, zobacz [strona kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Wiersz polecenia zdarzenia prekompilacyjnego**  
 Określa żadnych poleceń do wykonania przed rozpoczęciem kompilacji. Wpisanie polecenia długie, kliknij przycisk **Edytuj prekompilacyjnego** do wyświetlenia [prekompilacyjnego zdarzeń/po kompilacji — zdarzenie wiersza polecenia okno dialogowe](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
> [!NOTE]
>  Jeśli projekt jest aktualny i kompilacji nie zostanie wywołany, nie należy uruchamiać zdarzenia prekompilacyjnego.  
  
 **Wiersz polecenia zdarzenia po kompilacji**  
 Określa żadnych poleceń do wykonania po zakończeniu kompilacji. Wpisanie polecenia długie, kliknij przycisk **Edytuj postkompilacyjnego** do wyświetlenia **prekompilacyjnego zdarzeń/po kompilacji — zdarzenie wiersza polecenia okno dialogowe**.  
  
> [!NOTE]
>  Dodaj `call` instrukcję przed wszystkie postkompilacyjnego polecenia, które uruchamiają pliki bat. Na przykład `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Uruchomić zdarzenie mające miejsce po kompilacji**  
 Określa następujące warunki dla zdarzenia postkompilacyjnego do uruchomienia, jak pokazano w poniższej tabeli.  
  
|Opcja|Wynik|  
|------------|------------|  
|**Zawsze**|Zdarzenie mające miejsce po kompilacji zostanie uruchomiony niezależnie od tego, czy kompilacja zakończy się pomyślnie.|  
|**Pomyślnie kompilacji**|Zdarzenie mające miejsce po kompilacji zostanie uruchomiony, jeśli kompilacja zakończy się powodzeniem. W związku z tym zdarzeniem zostanie uruchomiony nawet w przypadku projektu, który jest aktualny, dopóki kompilacja zakończy się pomyślnie.|  
|**Gdy kompilacja aktualizuje wyjście projektu**|Zdarzenie mające miejsce po kompilacji zostanie uruchomiony tylko wtedy, gdy plik wyjściowy przez kompilator (.exe lub .dll) różni się od poprzedniego pliku danych wyjściowych kompilatora. W związku z tym zdarzenie mające miejsce po kompilacji nie jest uruchamiane, gdy projekt jest aktualny.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Porady: Określanie zdarzeń kompilacji (C#)](../../ide/how-to-specify-build-events-csharp.md)   
 [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)   
 [Kompilowanie i tworzenia](../../ide/compiling-and-building-in-visual-studio.md)