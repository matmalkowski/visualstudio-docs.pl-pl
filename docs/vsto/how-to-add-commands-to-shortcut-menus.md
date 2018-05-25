---
title: 'Porady: Dodawanie poleceń do menu skrótów'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: eb86a0c906ae2ae43308833cdec79195344abb7a
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Porady: Dodawanie poleceń do menu skrótów
  W tym temacie przedstawiono sposób dodawania poleceń do menu skrótów w aplikacji pakietu Office przy użyciu dodatku VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Aby dodać polecenia do menu skrótów w pakiecie Office  
  
1.  Dodaj **kodu XML wstążki** elementu na poziomie dokumentu i projektów dodatku VSTO. Aby uzyskać więcej informacji, zobacz [porady: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md). W  
  
2.  **Eksplorator rozwiązań**, wybierz pozycję **ThisAddin.cs** lub **ThisAddin.vb**.  
  
3.  Na pasku menu wybierz **widoku** > **kod**.  
  
     **Thisaddin —** klasy plik zostanie otwarty w edytorze kodu.  
  
4.  Dodaj następujący kod do **thisaddin —** klasy. Ten kod zastępuje `CreateRibbonExtensibilityObject` metodę i zwraca XML wstążki klasy do aplikacji pakietu Office.  
  
     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]  
  
5.  W **Eksploratora rozwiązań**, wybierz plik XML wstążki. Domyślnie, nosi nazwę pliku XML wstążki *Ribbon1.xml*.  
  
6.  Na pasku menu wybierz **widoku** > **kod**.  
  
     Plik xml wstążki, zostanie otwarty w edytorze kodu.  
  
7.  W edytorze kodu dodać kod XML, który opisuje menu skrótów i formant, który ma zostać dodany do menu skrótów.  
  
     W następującym przykładzie dodano przycisk menu i kontroli galerii do menu skrótów do dokumentu programu word. Identyfikator formantu tego menu skrótów jest ContextMenuText. Aby uzyskać pełną listę kontroli skrótu pakietu Office 2010 identyfikatory, zobacz [pliki Pomocy pakietu Office 2010: identyfikatory formantu interfejsu użytkownika fluent Office](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" />  
          <menu id="MySubMenu" label="My Submenu" >  
            <button id="MyButton2" label="Button on submenu" />  
          </menu>  
          <gallery id="galleryOne" label="My Gallery">  
            <item id="item1" imageMso="HappyFace" />  
            <item id="item2" imageMso="HappyFace" />  
            <item id="item3" imageMso="HappyFace" />  
            <item id="item4" imageMso="HappyFace" />  
          </gallery>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
8.  W **Eksploratora rozwiązań**, wybierz **MyRibbon.cs** lub **MyRibbon.vb**.  
  
9. Dodaj metodę wywołania zwrotnego `Ribbon1` klasy dla każdego formantu, który ma obsługiwać.  
  
     Następujące dojścia metody wywołania zwrotnego **przycisk Moje** przycisku. Ten kod dodaje ciąg do aktywnego dokumentu w bieżącej lokalizacji kursor.  
  
     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]  
  
## <a name="see-also"></a>Zobacz także  
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Wskazówki: Tworzenie menu skrótów dla zakładek](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Dostosowywanie menu kontekstowe w pakiecie Office 2010](http://go.microsoft.com/fwlink/?LinkId=182186)  
  