---
title: "Odczytywanie modeli i diagramów w innych wersjach programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: "20"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.openlocfilehash: 704c69efa4e0495a1a4aa7545fa6ba100488afe9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Odczytywanie modeli i diagramów w innych wersjach programu Visual Studio
Podczas otwierania modelu w wersji programu Visual Studio, która nie obsługuje tworzenia modelu, model zostanie otwarty w trybie tylko do odczytu. W tym trybie można zmienić układ diagramy, ale nie można zmienić modelu na model.  
  
 Aby dowiedzieć się, które wersje programu Visual Studio obsługują tworzenie modelu, zobacz [obsługę wersji architektura i modelowanie narzędzia](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="obtaining-access-to-a-model-and-diagrams"></a>Uzyskiwanie dostępu do modelu i diagramów  
 Aby odczytać diagram zależności, musi najpierw za pomocą programu Visual Studio Otwórz projekt modelowania, a następnie Otwórz diagram w niej.  
  
 Z tego powodu jeśli chcesz odczytać diagramu zależności musi masz również dostęp do projektu modelowania, w której został utworzony. Można to zrobić po zalogowaniu się do projektu z [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)], lub uzyskując kopię plików projektu.  
  
> [!NOTE]
>  To nie ma zastosowania do kodu map i .NET klasy diagramy wygenerowane z kodu. Niezależnie od projektu modelowania diagramów jest możliwy.  
  
 Aby odczytać diagram zależności, minimalny zestaw plików, które są potrzebne jest następujący:  
  
-   Diagram dwa pliki do diagramu, który chcesz odczytać, na przykład **MyDiagram.classdiagram i MyDiagram.classdiagram.layout**.  
  
    > [!NOTE]
    >  Dla diagramów zależności, również powinny mieć pliku o nazwie *MyDiagram***. layerdiagram.suppressions**.  
  
-   Plik projektu modelowania (**MyModel.modelproj**)  
  
-   Plik modelu głównym (**ModelDefinition\MyModel.uml**)  
  
-   Pliki pakietu dla dowolnego pakietu, do którego odwołuje się na diagramie (**ModelDefinition\MyPackage.uml**)  
  
## <a name="changes-that-you-can-make-in-read-only-mode"></a>Zmiany wprowadzone w trybie tylko do odczytu  
 Po otwarciu modelu i jego diagramów w wersji programu Visual Studio, która nie obsługuje tworzenia modelu nie można zmienić modelu. Oznacza to, że nie można zmienić elementów i relacji, które są wyświetlane na diagramach lub w Eksploratorze modelu. Jednak ułatwia pewne zmiany w układzie diagramów:  
  
-   Rozmieszczanie kształtów i łączników na diagramie.  
  
-   Rozwijanie i zwijanie kształtów.  
  
 Można zapisać zmian. Jeśli chcesz zmiany były widoczne dla innych użytkowników, musisz co najmniej wysłać zaktualizowane **.layout** plików.  
  
##  <a name="RelatedTopics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md)|Diagram warstwowy pokazuje strukturę ogólną architektury. Gdy jest zapisywany kod, mogą zostać automatycznie zweryfikowany względem diagramu warstwowego.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)