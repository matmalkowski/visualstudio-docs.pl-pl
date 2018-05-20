---
title: 'Porady: aplikacje pakietu Office docelowym za pośrednictwem podstawowe zestawy międzyoperacyjne'
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
ms.openlocfilehash: 32ff157e3986836ac13472c4a9ed8a7b01f06e04
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Porady: aplikacje pakietu Office docelowym za pośrednictwem podstawowe zestawy międzyoperacyjne
  Podczas tworzenia nowego projektu pakietu Office Visual Studio automatycznie dodaje odwołania do programu Microsoft Office podstawowe zestawy międzyoperacyjne (PIAs), które są wymagane, aby skompilować projekt. Należy dodać odwołania do innych PIAs w następujących scenariuszach:  
  
-   Chcesz używać funkcji innych aplikacji pakietu Microsoft Office w projekcie. Na przykład można użyć funkcji programu Microsoft Office Excel w projekcie dla programu Microsoft Office Word.  
  
-   Chcesz zautomatyzować aplikacji Microsoft Office, które nie mają dedykowanych projekty w programie Visual Studio, takich jak Microsoft Office Access.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Aby dodać odwołanie do podstawowego zestawu międzyoperacyjnego  
  
1.  Otwórz projekt pakietu Office i wybierz nazwę projektu w **Eksploratora rozwiązań**.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.  
  
3.  Na **Framework** , a następnie wybierz PIA w **nazwa składnika** listy. Aby uzyskać więcej informacji o dostępnych podstawowe zestawy międzyoperacyjne Microsoft Office, zobacz [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md).  
  
     Jeśli obiekty docelowe projektu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, **Osadź typy międzyoperacyjne** ma ustawioną wartość właściwości dla odwołania do zestawu **True** domyślnie. Za pomocą tego ustawienia, rozwiązanie nie wymaga PIA na komputerach użytkowników końcowych. Aby uzyskać więcej informacji, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).  
  
    > [!NOTE]  
    >  W projektach pakietu Office przy użyciu dodać odwołania do pakietu Office PIAs **.NET** karty **Dodaj odwołanie** okna dialogowego zamiast **COM** kartę. Aby uzyskać więcej informacji, zobacz [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md).  
  
4.  Kliknij przycisk **OK**.  
  
     Nazwa zestawu jest wyświetlana w **odwołania** folderu **Eksploratora rozwiązań**.  
  
## <a name="see-also"></a>Zobacz także  
 [Podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md)   
 [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)   
 [Opracowywania rozwiązań pakietu Office](../vsto/developing-office-solutions.md)   
 [Porady: podstawowe zestawy międzyoperacyjne pakietu Office instalacji](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  