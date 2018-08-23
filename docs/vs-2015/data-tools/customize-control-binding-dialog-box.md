---
title: Dostosuj powiązania okno dialogowe kontrolki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.datauicustomization
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Customize Control Binding dialog box
ms.assetid: abcc0be3-a18e-4f47-b354-d6b0c618e087
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4d47fe3962651db91dcfdf6e59653db539a9f44b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679801"
---
# <a name="customize-control-binding-dialog-box"></a>Dostosuj powiązania kontrolki — Okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj **Dostosuj powiązania kontrolki** okno dialogowe, aby określić, które kontrolki są dostępne dla elementów w [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
 Każdy element na **źródeł danych** okno ma skojarzone listy elementów sterujących, które może być powiązana z elementem. Formanty, które są dostępne dla każdego elementu są określane przez typ danych elementu. Każdy typ danych ma listę prawidłowe skojarzonych formantów, zdefiniowane w tym oknie, w tym domyślny formant.  
  
 Przed przeciągnięciem elementu do powierzchni projektu, aby utworzyć formant powiązany z danymi, można wybrać, które określają, aby utworzyć. Jeśli przeciągniesz element **źródeł danych** okna na powierzchni projektowej bez zaznaczania kontrolki, domyślny formant dla typu danych wybrany element zostanie dodany do powierzchni projektowej.  
  
 Aby uzyskać więcej informacji o sposobie używania to okno dialogowe, aby dostosować listę formantów dla elementów w **źródeł danych** okna, zobacz [Dodawanie niestandardowych formantów do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Typ danych**  
 Wyświetla listę typów, które skojarzysz z kontrolkami:  
  
-   Tabele, jednostek i obiektów, które są reprezentowane jako **[lista]** typów.  
  
-   Kolumny lub właściwości publicznej, jednostek i obiektów są reprezentowane jako typ danych rzeczywistych kolumny lub właściwości w podstawowym magazynie danych.  
  
-   Obiekty kształtów zdefiniowane przez użytkownika są reprezentowane jako **(inne)**. Na przykład jeśli aplikacja ma formant niestandardowy, który wyświetla dane z więcej niż jedną właściwość obiektu, wybierz pozycję **(inne)** typ danych dla formantu.  
  
 **Skojarzonych formantów**  
 Wyświetla listę elementów sterujących, które można skojarzyć z określonego typu danych. Jeśli chcesz skojarzyć określonego formantu z typem danych wybranym w **— typ danych** , wybierz odpowiednie pole wyboru na liście. Wyczyść pole wyboru, aby usunąć skojarzenie. Sprawdzane, formanty są wyświetlane w menu skrótów przedstawiony przez **źródeł danych** okna dla elementu typu powiązane dane.  
  
 Formanty można dodać do listy, dodając formanty, które mają jeden z kilku atrybutów powiązania danych, które mają **przybornika**. Aby uzyskać więcej informacji, zobacz [Dodawanie niestandardowych formantów do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 **Ustaw wartość domyślną**  
 Przypisuje wybrany formant typ jako domyślny dla elementów typu wybranych danych. Domyślny formant, który jest wyświetlany jako pierwszy wybór w menu skrótów przedstawiony przez **źródeł danych** okna dla elementu. Tylko jeden formant typu mogą być przypisane jako wartość domyślna dla typu danych.  
  
 **Wyczyść domyślne**  
 Usuwa oznaczenie formantu jako domyślne dla wybranego typu danych. Jeśli nie istnieje domyślny dla wybranego typu danych, **[Brak]** jest wyświetlany jako pierwszy wybór w menu skrótów przedstawiony przez **źródeł danych** okna dla elementu skojarzonego typu.  
  
## <a name="see-also"></a>Zobacz też  
 [Okno źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)   
 [Powiązywanie kontrolek formularzy Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Dodawanie niestandardowych formantów do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md)   
 [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)