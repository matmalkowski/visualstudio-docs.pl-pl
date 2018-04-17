---
title: Rozszerzanie diagramy zależności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b359507946a68ee457d4840fc8652f7f48e3e11a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="extend-dependency-diagrams"></a>Rozszerzanie diagramy zależności
Można napisać kod, aby tworzenie i aktualizowanie diagramami zależności oraz zweryfikowanie struktury kodu źródłowego przed diagramy zależności w programie Visual Studio. Możesz dodać polecenia, które są wyświetlane w menu skrótów (context) diagramy, Dostosowywanie gestów przeciągania i upuszczania i uzyskać dostęp do modelu warstwy z szablonów tekstowych. Można spakować tych rozszerzeń w Visual Studio integracji rozszerzenia (VSIX) i rozproszyć je do innych użytkowników programu Visual Studio.  
  
 Aby uzyskać więcej informacji o zależnościach diagramy zobacz:  
  
-   [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)  
  
-   [Diagramy zależności: Wskazówki](../modeling/layer-diagrams-guidelines.md)  
  
-   [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)  
  
##  <a name="prereqs"></a> Wymagania  
 Musi mieć zainstalowane na komputerze, na którym ma zostać opracowywania rozszerzeń warstwy następujące elementy:  
  
-   Visual Studio  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md)  
  
-   Modelowanie zestawu SDK dla programu Visual Studio  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
 Musi mieć odpowiedniej wersji programu Visual Studio na komputerze, na którym chcesz uruchomić rozszerzenia warstwy. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzenia modelu warstwy](../modeling/deploy-a-layer-model-extension.md).  
  
 Aby dowiedzieć się, które wersje programu Visual Studio obsługują diagramy zależności, zobacz [obsługę wersji architektura i modelowanie narzędzia](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Dodawanie poleceń i gestów do diagramów zależności](../modeling/add-commands-and-gestures-to-layer-diagrams.md)  
  
 [Dodawanie niestandardowej walidacji architektury do diagramów zależności](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)  
  
 [Dodawanie właściwości niestandardowych do diagramów zależności](../modeling/add-custom-properties-to-layer-diagrams.md)  
  
 [Nawigowanie i aktualizowanie modeli warstw w kodzie programu](../modeling/navigate-and-update-layer-models-in-program-code.md)  
  
 [Wdrażanie rozszerzenia modelu warstwy](../modeling/deploy-a-layer-model-extension.md)  
  
 [Rozwiązywanie problemów z rozszerzeniami dla diagramów zależności](../modeling/troubleshoot-extensions-for-layer-diagrams.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md)   
 [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)   
 [Tworzenie diagramów zależności w kodzie](../modeling/create-layer-diagrams-from-your-code.md)   
 [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)   
