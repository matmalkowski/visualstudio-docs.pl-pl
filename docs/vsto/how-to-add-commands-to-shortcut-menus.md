---
title: "Porady: Dodawanie poleceń do menu skrótów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
ms.assetid: 9a848817-db11-4294-8f6f-9181ab87aadd
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 40b2bbb7c7b86665790a06feed288b0dd37272df
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Porady: dodawanie poleceń do menu skrótów
  W tym temacie przedstawiono sposób dodawania poleceń do menu skrótów w aplikacji pakietu Office przy użyciu dodatku VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Aby dodać polecenia do menu skrótów w pakiecie Office  
  
1.  Dodaj **kodu XML wstążki** elementu na poziomie dokumentu i projektów dodatku VSTO. Aby uzyskać więcej informacji, zobacz [porady: uzyskiwanie uruchomiona Dostosowywanie wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md). W  
  
2.  **Eksplorator rozwiązań**, wybierz pozycję **ThisAddin.cs** lub **ThisAddin.vb**.  
  
3.  Na pasku menu wybierz **widoku**, **kod**.  
  
     **Thisaddin —** klasy plik zostanie otwarty w edytorze kodu.  
  
4.  Dodaj następujący kod do **thisaddin —** klasy. Ten kod zastępuje metodę CreateRibbonExtensibilityObject i zwraca klasy XML wstążki do aplikacji pakietu Office.  
  
     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]  
  
5.  W **Eksploratora rozwiązań**, wybierz plik XML wstążki. Domyślnie plik XML wstążki nosi nazwę Ribbon1.xml.  
  
6.  Na pasku menu wybierz **widoku**, **kod**.  
  
     Plik xml wstążki, zostanie otwarty w edytorze kodu.  
  
7.  W edytorze kodu dodać kod XML, który opisuje menu skrótów i formant, który ma zostać dodany do menu skrótów.  
  
     W następującym przykładzie dodano przycisk menu i kontroli galerii do menu skrótów do dokumentu programu word. Identyfikator formantu tego menu skrótów jest ContextMenuText. Aby uzyskać pełną listę kontroli skrótu pakietu Office 2010 identyfikatory, zobacz [pliki Pomocy pakietu Office 2010: identyfikatory formantu interfejsu użytkownika Office Fluent](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
    ```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Wskazówki: Tworzenie menu skrótów dla zakładek](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Dostosowywanie menu kontekstowe w pakiecie Office 2010](http://go.microsoft.com/fwlink/?LinkId=182186)  
  
  