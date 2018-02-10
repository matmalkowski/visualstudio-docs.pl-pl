---
title: "Odczytywanie modeli i diagramów w innych wersjach programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- models, versions of Visual Studio
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: bec543b7adbf4ea27dca40be4ba51dc0eb622669
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
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
    >  Dla diagramów zależności, również powinny mieć pliku o nazwie * MyDiagram ***. layerdiagram.suppressions**.  
  
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
|[Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)|Diagram warstwowy pokazuje strukturę ogólną architektury. Gdy jest zapisywany kod, mogą zostać automatycznie zweryfikowany względem diagramu warstwowego.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)