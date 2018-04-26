---
title: Projektant przepływu pracy — wybierz operację, okno dialogowe (starsze)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fed4353771edc5f9cc1bb239424b0e7015acd84a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="choose-operation-dialog-box-legacy"></a>Wybierz operację, okno dialogowe (starsze)

W tym temacie opisano sposób użycia **wybierz operację** okno dialogowe w starszej wersji projektanta przepływów pracy systemu Windows. Starsze projektanta przepływów pracy należy używać wtedy, gdy konieczne objęcie .NET Framework w wersji 3.5 lub WinFX.

 **Wybierz operacji** okno dialogowe służy do wybierania operacji do skojarzenia z <xref:System.Workflow.Activities.ReceiveActivity> działania lub <xref:System.Workflow.Activities.SendActivity> działania. Aby uzyskać więcej informacji o korzystaniu z tego okna dialogowego z tych działań, zobacz [jak: Implementowanie operacja kontraktu usługi WCF (starsze)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) i [jak: wywołaj operację kontraktu usługi WCF (starsze)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).

 W poniższej tabeli opisano elementy interfejsu użytkownika **wybierz operacji** okno dialogowe.

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**Dodaj umowy**|Tworzy nowego kontraktu. Możesz zdefiniować nowe operacje tego kontraktu. (To jest używany z <xref:System.Workflow.Activities.ReceiveActivity> tylko.)|
|**Operacja dodania**|Dodaje nowe operacje do nowego kontraktu, który został utworzony w **wybierz operacji** okno dialogowe. **Uwaga:** nowych operacji można dodać tylko do umów, które zostały utworzone za pomocą **wybierz operacji** okno dialogowe. <br /><br /> (To jest używany z <xref:System.Workflow.Activities.ReceiveActivity> tylko.)|
|**Importuj...**|Importuje wcześniej zdefiniowanego kontraktu i umożliwia wybranie operacji z tej Umowy.|
|**Nazwa operacji**|Nazwa aktualnie wybranej operacji. To pole tekstowe jest dostępny do edycji tylko wtedy, gdy utworzono operację za pośrednictwem **wybierz operacji** okno dialogowe.|
|**Parametry**|Karta z definicjami parametrów dla aktualnie wybranej operacji. **Uwaga:** definicjami parametrów można zmienić tylko wtedy, gdy utworzono operację za pośrednictwem **wybierz operacji** okno dialogowe.|
|**Właściwości**|Karta zawierająca <xref:System.Net.Security.ProtectionLevel> ustawień komunikatów wysyłanych między klientem a usługą. **Uwaga:** na tej karcie jest włączona tylko wtedy, gdy utworzono operację za pośrednictwem **wybierz operacji** okno dialogowe.|
|**Uprawnienia**|Karta zawierająca <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> i <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> właściwości użytkowników uprawnionych do wywołania tej operacji. Na przykład, jeśli użytkownicy z grupy administratorów były dozwolone tylko do wywołania tej operacji, a następnie piszesz "Administratorzy" **roli** pola tekstowego.<br /><br /> Na tej karcie jest włączony dla obu operacji, został utworzony za pomocą **ChooseOperation** okno dialogowe i operacje, które zostały zaimportowane do **importu** przycisku.|

> [!NOTE]
> **Wybierz operacji** wyświetlane okno dialogowe tylko umów lub operacje, które są używane przez inne <xref:System.Workflow.Activities.SendActivity> działań w przepływie pracy. Podobnie **wybierz operacji** okno dialogowe <xref:System.Workflow.Activities.ReceiveActivity> działania są wyświetlane tylko umów albo operacje, które są używane przez inne **ReceiveActivity** działań w przepływie pracy.

## <a name="see-also"></a>Zobacz także

- [Porady: Implementowanie operacja kontraktu usługi WCF (starsze)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)
- [Porady: wywoływanie operacja kontraktu usługi WCF (starsze)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)
- [Starsza wersja projektanta pomocy interfejsu użytkownika programu Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)