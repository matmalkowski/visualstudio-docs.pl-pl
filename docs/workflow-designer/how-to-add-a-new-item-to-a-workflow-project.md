---
title: 'Projektant przepływu pracy — porady: Dodawanie nowego elementu do projektu przepływu pracy'
ms.date: 06/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c3f1202c87986eab6af899a3d4c3b7a5f62e5af6
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757682"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Porady: Dodawanie nowego elementu do projektu przepływu pracy

Po utworzeniu projektu przepływu pracy, można dodać działania przepływu pracy, projektantów i innych znanych elementów programu Visual Studio do projektu.

W poniższej tabeli wymieniono elementy programu Windows Workflow Foundation (WF), które można dodać do projektu przepływu pracy:

|Nazwa|Opis|
|----------|-----------------|
|Działanie|Działanie składa się z innymi działaniami. Wybranie tego elementu dodaje tego samego pliku XAML do projektu, jak można uzyskać po wybraniu **Biblioteka działań** szablonu dla nowego projektu. Aby uzyskać więcej informacji na temat na tej procedury, zobacz [porady: Tworzenie biblioteki działań](../workflow-designer/how-to-create-an-activity-library.md).|
|Projektant działań|Projektant umożliwiający dostosowanie środowiska czasu projektowania działania. Wybranie tego elementu dodaje tych samych plików do projektu, jak można uzyskać po wybraniu **Biblioteka Projektant działań** szablonu dla nowego projektu. Aby uzyskać więcej informacji na temat na tej procedury, zobacz [porady: Tworzenie biblioteki projektanta działania](../workflow-designer/how-to-create-an-activity-designer-library.md).|
|Działania związane z kodem|Działanie z logiką wykonywania zapisaną w kodzie. Pliku kodu źródłowego za pomocą zastąpienia z <xref:System.Activities.CodeActivity.Execute%2A> metoda została już wygenerowana automatycznie.|
|Usługi przepływu pracy WCF|A [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] usługi utworzone przy użyciu działań przepływu pracy. Wybranie tego elementu dodaje tych samych plików do projektu, jak można uzyskać po wybraniu **aplikacji usługi przepływu pracy WCF** szablonu dla nowego projektu. Aby uzyskać więcej informacji na temat tej procedury, zobacz [porady: tworzenie aplikacji usługi przepływu pracy WCF](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Aby dodać nowy element do projektu przepływu pracy

1. Na **projektu** menu, wybierz opcję **Dodaj nowy element**.

   **Dodaj nowy element** zostanie otwarte okno dialogowe.

1. W okienku po lewej stronie wybierz **przepływu pracy** kategorii, a następnie wybierz szablon elementu przepływu pracy.

   > [!NOTE]
   > Jeśli nie widzisz **przepływu pracy** kategorii, wcześniejszej instalacji **Windows Workflow Foundation** składnika programu Visual Studio 2017 r. Aby uzyskać szczegółowe instrukcje, zobacz [zainstalować program Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Wprowadź nazwę dla elementu w **nazwa** u dołu okna dialogowego.

1. Wybierz **Dodaj** można dodać elementu do projektu.

## <a name="see-also"></a>Zobacz także

- [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)