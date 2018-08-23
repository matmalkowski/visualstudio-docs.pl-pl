---
title: Strona zdarzenia kompilacji, Projektant projektu (C#) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 86ada1d23490c4e154cbdb7ba17f81acbee1796a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42697005"
---
# <a name="build-events-page-project-designer-c"></a>Strona Zdarzenia kompilacji, Projektant projektu (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [zdarzenia Stroka kompilacji, Projektant projektu (C#)](https://docs.microsoft.com/visualstudio/ide/reference/build-events-page-project-designer-csharp).  
  
  
Użyj **zdarzenia kompilacji** strony **projektanta projektu** do określenia instrukcje dotyczące konfiguracji kompilacji. Można również określić warunki, w których są uruchamiane wszystkie zdarzenia mające miejsce po kompilacji. Aby uzyskać więcej informacji, zobacz [jak: Specify Build Events (C#)](../../ide/how-to-specify-build-events-csharp.md)i [jak: Specify Build Events (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Konfiguracja**  
 Ta kontrolka nie jest edytowalny na tej stronie. Aby uzyskać opis tego formantu, zobacz [Stroka kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Platforma**  
 Ta kontrolka nie jest edytowalny na tej stronie. Aby uzyskać opis tego formantu, zobacz [Stroka kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Wiersz polecenia zdarzenia sprzed kompilacji**  
 Określa wszystkie polecenia do wykonania przed rozpoczęciem kompilacji. Do typu long polecenia, kliknij przycisk **Edytuj prekompilacji** do wyświetlenia [prekompilacji zdarzeń/po kompilacji — zdarzenie wiersza polecenia okno dialogowe](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
> [!NOTE]
>  Jeśli projekt jest aktualny, a nie kompilacja zostaje wyzwolona, nie należy uruchamiać zdarzenia prekompilacyjnego.  
  
 **Wiersz polecenia zdarzenia po kompilacji**  
 Określa wszystkie polecenia do wykonania po zakończeniu kompilacji. Do typu long polecenia, kliknij przycisk **edytować po kompilacji** do wyświetlenia **prekompilacji zdarzeń/po kompilacji — zdarzenie wiersza polecenia okno dialogowe**.  
  
> [!NOTE]
>  Dodaj `call` instrukcję przed polecenia wszystkich wykonywanych po kompilacji, które uruchamiają pliki bat. Na przykład `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Uruchom zdarzenie po kompilacji**  
 Określa następujące warunki dla zdarzenia postkompilacyjnego do uruchomienia, jak pokazano w poniższej tabeli.  
  
|Opcja|Wynik|  
|------------|------------|  
|**zawsze**|Zdarzenie po kompilacji zostaną uruchomione niezależnie od tego, czy kompilacja zakończy się pomyślnie.|  
|**W przypadku pomyślnej kompilacji**|Zdarzenie po kompilacji będzie działać, jeśli kompilacja zakończy się pomyślnie. W związku z tym zdarzenia uruchomią się nawet w przypadku projektu, który jest aktualne, tak długo, jak kompilacja zakończy się pomyślnie.|  
|**Gdy kompilacja aktualizuje dane wyjściowe projektu**|Zdarzenie po kompilacji zostanie uruchomiona tylko w sytuacji, gdy plik wyjściowy kompilatora (.exe lub .dll) różni się od poprzedniego pliku danych wyjściowych kompilatora. W związku z tym zdarzenia postkompilacyjnego nie zostanie uruchomione, gdy projekt jest aktualny.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Porady: Określanie zdarzeń kompilacji (C#)](../../ide/how-to-specify-build-events-csharp.md)   
 [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)   
 [Kompilowanie i tworzenie](../../ide/compiling-and-building-in-visual-studio.md)



