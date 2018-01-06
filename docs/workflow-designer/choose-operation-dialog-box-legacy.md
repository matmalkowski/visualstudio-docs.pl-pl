---
title: "Wybierz operację, okno dialogowe (starsze) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 2db745d34c86e4b0aa5639872106096421044bce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="choose-operation-dialog-box-legacy"></a>Wybierz operację, okno dialogowe (starsze)
W tym temacie opisano sposób użycia **wybierz operacji** okno dialogowe w starszych [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]. Użyj starszego [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] konieczność docelowy: [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
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
>  **Wybierz operacji** wyświetlane okno dialogowe tylko umów lub operacje, które są używane przez inne <xref:System.Workflow.Activities.SendActivity> działań w przepływie pracy. Podobnie **wybierz operacji** okno dialogowe <xref:System.Workflow.Activities.ReceiveActivity> działania są wyświetlane tylko umów albo operacje, które są używane przez inne **ReceiveActivity** działań w przepływie pracy.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Implementowanie operacja kontraktu usługi WCF (starsze)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Porady: wywoływanie operacja kontraktu usługi WCF (starsze)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Starsza wersja projektanta pomocy interfejsu użytkownika programu Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)