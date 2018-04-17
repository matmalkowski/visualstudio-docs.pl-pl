---
title: 'Porady: aplikacje pakietu Office za pośrednictwem podstawowe zestawy międzyoperacyjne docelowe | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bfe02a06403621c2429dd8be965b3ab1b5c41b2c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Porady: konfigurowanie pod kątem aplikacji pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych
  Podczas tworzenia nowego projektu pakietu Office Visual Studio automatycznie dodaje odwołania do programu Microsoft Office podstawowe zestawy międzyoperacyjne (PIAs), które są wymagane, aby skompilować projekt. Należy dodać odwołania do innych PIAs w następujących scenariuszach:  
  
-   Chcesz używać funkcji innych aplikacji pakietu Microsoft Office w projekcie. Na przykład można użyć funkcji programu Microsoft Office Excel w projekcie dla programu Microsoft Office Word.  
  
-   Chcesz zautomatyzować aplikacji Microsoft Office, które nie mają dedykowanych projekty w programie Visual Studio, takich jak Microsoft Office Access.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Aby dodać odwołanie do podstawowego zestawu międzyoperacyjnego  
  
1.  Otwórz projekt pakietu Office i wybierz nazwę projektu w **Eksploratora rozwiązań**.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.  
  
3.  Na **Framework** , a następnie wybierz PIA w **nazwa składnika** listy. Aby uzyskać więcej informacji o dostępnych podstawowe zestawy międzyoperacyjne Microsoft Office, zobacz [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md).  
  
     Jeśli obiekty docelowe projektu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, **Osadź typy międzyoperacyjne** ma ustawioną wartość właściwości dla odwołania do zestawu **True** domyślnie. Za pomocą tego ustawienia, rozwiązanie nie wymaga PIA na komputerach użytkowników końcowych. Aby uzyskać więcej informacji, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).  
  
    > [!NOTE]  
    >  W projektach pakietu Office przy użyciu dodać odwołania do pakietu Office PIAs **.NET** karty **Dodaj odwołanie** okna dialogowego zamiast **COM** kartę. Aby uzyskać więcej informacji, zobacz [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md).  
  
4.  Kliknij przycisk **OK**.  
  
     Nazwa zestawu jest wyświetlana w **odwołania** folderu **Eksploratora rozwiązań**.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md)   
 [Pisanie kodu dla rozwiązań pakietu Office](../vsto/writing-code-in-office-solutions.md)   
 [Tworzenie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)   
 [Instrukcje: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  