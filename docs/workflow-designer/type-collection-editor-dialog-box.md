---
title: Okno dialogowe Edytor kolekcji typu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 77de1cdcffc1303a439afe743cdfd52b121779d7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="type-collection-editor-dialog-box"></a>Okno dialogowe Edytor kolekcji typów

**Edytora kolekcji typu** okno dialogowe służy do dodawania znanych typów do **wysyłania** i **Receive** działań. To okno dialogowe służy również do argumentów typu ogólnego, aby dodać **InvokeMethod** działania. Gdy jest używany dla **wysyłania** i **Receive** działania, aby dodać znanych typów, **edytora kolekcji typu** okno dialogowe wymaga dodatków typu być unikatowe. Jeśli jest dodać zduplikowany typ i zmiana zostaje zatwierdzona, klikając **OK**, jest zwracany komunikat o błędzie. Gdy jest używany dla **InvokeMethod** działanie, aby dodać argumentów typu ogólnego **edytora kolekcji typu** okno dialogowe umożliwia dodanie zduplikowane typy.

Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](/dotnet/framework/wcf/feature-details/data-contract-known-types).

W poniższej tabeli opisano elementy interfejsu użytkownika **kolekcji typu** okno dialogowe.

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**Lista typów**|Lista typów, które zostały dodane lub usunięte.|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Aby przełączyć się Edytor kolekcji typów do wysyłania i odbierania działań

1.  Wybierz **wysyłania** lub **Receive** działania w widoku Projekt.

2.  Naciśnij klawisz **F4** można wyświetlić **właściwości** okna.

3.  W **właściwości** , kliknij wielokropek przycisk Dalej, aby **element KnownTypes** właściwości.

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Aby wyświetlić się Edytor kolekcji typu dla metody InvokeMethod działania

1.  Wybierz **InvokeMethod** działania w widoku Projekt.

2.  Naciśnij klawisz **F4** można wyświetlić **właściwości** okna.

3.  W **właściwości** , kliknij wielokropek przycisk Dalej, aby **GenericTypeArguments** właściwości.