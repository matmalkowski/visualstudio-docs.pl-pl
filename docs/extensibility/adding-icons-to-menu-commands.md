---
title: "Dodawanie ikon do poleceń Menu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 06d90b5174cc9ff2d09d7ccba8b2f39bc1d2a077
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="adding-icons-to-menu-commands"></a>Dodawanie ikon do poleceń Menu
Polecenia może występować w zarówno menu i pasków narzędzi. Na paskach narzędzi jest typowe dla polecenia mają być wyświetlane tylko ikona (Aby zaoszczędzić miejsce) podczas menu polecenie zwykle wyświetlany jest zarówno ikony, jak i tekstu.  
  
 Ikony są 16 pikseli szerokości i wysokości 16 pikseli i może być 8-bitowej głębi kolorów (256 kolorów) lub głębi kolorów 32-bitowych (kolor true). 32-bitowe ikony są preferowane. Ikony zwykle ułożone w jednym wierszu poziomy w jednym mapy bitowej, mimo że wiele map bitowych są dozwolone. Ta mapa bitowa jest zadeklarowany w pliku vsct wraz z poszczególnych ikon dostępne w pliku mapy bitowej. Zobacz odwołanie do [Element map bitowych](../extensibility/bitmaps-element.md) więcej szczegółów.  
  
## <a name="adding-an-icon-to-a-command"></a>Dodawanie ikon do polecenia  
 W poniższej procedurze przyjęto, że masz istniejący projekt pakiet VSPackage za pomocą polecenia menu. Aby dowiedzieć się, jak to zrobić, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Utwórz mapę bitową o głębi kolorów 32-bitowej. Ikona jest zawsze 16 x 16, więc tej mapy bitowej musi być 16 pikseli i wielokrotnością 16 pikseli szerokości.  
  
     Każda z ikon jest umieszczona na mapę bitową obok siebie w jednym wierszu. Umożliwia wskazanie miejsca przezroczystość w każdej ikony kanału alfa.  
  
     Jeśli używasz 8-bitowej głębi kolorów, użyj magenta, `RGB(255,0,255)`, jako przezroczystość. Jednak ikon koloru 32-bitowych są preferowane.  
  
2.  Skopiuj plik ikony do katalogu zasobów w projekcie pakiet VSPackage. W Eksploratorze rozwiązań należy dodać ikony do projektu. (Wybierz zasoby, w menu kontekstowym kliknij przycisk Dodaj, a następnie istniejący element i wybrać plik ikony.)  
  
3.  Otwórz plik vsct w edytorze.  
  
4.  Dodaj `GuidSymbol` elementu o nazwie **testIcon**. Utwórz identyfikator GUID (**narzędzi / Create GUID**, a następnie wybierz pozycję **Format rejestru** i kliknij pozycję Kopiuj) i wklej ją do `value` atrybutu. Wynik powinien wyglądać następująco:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  Dodaj `<IDSymbol>` ikony. `name` Atrybut jest identyfikator ikony i `value` wskazuje pozycji na pasku, jeśli istnieje. Jeśli istnieje tylko jedna ikona, Dodaj 1. Wynik powinien wyglądać następująco:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  Utwórz `<Bitmap>` w `<Bitmaps>` sekcji pliku vsct do reprezentowania mapy bitowej zawierającego ikony.  
  
    -   Ustaw `guid` wartość na nazwę `<GuidSymbol>` elementu utworzonego w poprzednim kroku.  
  
    -   Ustaw `href` wartość do ścieżki względnej pliku mapy bitowej (w tym przypadku **zasobów\\< nazwa pliku ikony\>**.  
  
    -   Ustaw `usedList` wartość IDSymbol utworzony wcześniej. Ten atrybut określa listę rozdzielanych przecinkami ikon do użycia w pakiecie VSPackage. Ikony nie ma na liście są wykluczone formularza kompilacji.  
  
         Blok mapy bitowej powinien wyglądać następująco:  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  W istniejących `<Button>` , ustaw `Icon` elementu wartości GUIDSymbol i IDSymbol utworzony wcześniej. Oto przykład elementu przycisk tymi wartościami:  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  Twoje ikona testowa. Skompiluj projekt i Rozpocznij debugowanie. W eksperymentalnym wystąpieniu znaleźć polecenia. Ikona powinny mieć zostały dodane.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)   
 [Odwołanie do schematu XML VSCT](../extensibility/vsct-xml-schema-reference.md)