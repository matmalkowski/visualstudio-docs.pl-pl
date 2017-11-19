---
title: "Konfiguracja wyświetlania okna narzędzia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7ab5cef6fb45d60be8be8d1db6b160079633ed4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="tool-window-display-configuration"></a>Konfiguracja wyświetlania okna narzędzi
Kiedy pakiet VSPackage rejestruje okna narzędzia, pozycja domyślny rozmiar, styl dokowania i inne informacje widoczność określono opcjonalnych wartości. Aby uzyskać więcej informacji o rejestracji okna narzędzia, zobacz [okna narzędzi w rejestrze](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>Wyświetl informacje o oknie  
 Konfiguracja podstawowa ekranu okna narzędzia są przechowywane w sześciu opcjonalnych wartości:  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|Nazwa|REG_SZ|"Krótkiej nazwy tu"|Krótką nazwę, która opisuje okna narzędzia. Używana tylko w przypadku odwołania w rejestrze.|  
|Float|REG_SZ|"X1, Y1, X2, Y2"|Cztery wartości rozdzielonych przecinkami. X1, Y1 jest współrzędne górnego lewego rogu okna narzędzia. X2, Y2 jest współrzędną prawym dolnym rogu. Wszystkie wartości są we współrzędnych ekranu.|  
|Styl|REG_SZ|"MDI"<br /><br /> "Float"<br /><br /> "Połączone"<br /><br /> "Na kartach"<br /><br /> "AlwaysFloat"|Słowo kluczowe Określanie początkowej wyświetlanie stanu okna narzędzia.<br /><br /> "MDI" = zadokowane okna MDI.<br /><br /> "Float" = zmiennoprzecinkową.<br /><br /> "Połączone" = połączone z innym oknie (określone we wpisie okno).<br /><br /> "Na kartach" = połączone z innego okna narzędzia.<br /><br /> "AlwaysFloat" = nie może być zadokowany.<br /><br /> Aby uzyskać więcej informacji zobacz sekcję komentarze poniżej.|  
|Okno|REG_SZ|*\<IDENTYFIKATOR GUID >*|Identyfikator GUID okna, do którego można połączone lub kartach okna narzędzia. Identyfikator GUID może należeć do jednego z własnego systemu windows lub jeden z przedziałów czasu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE.|  
|Orientacja|REG_SZ|"Lewo"<br /><br /> "Prawej"<br /><br /> "Top"<br /><br /> "Bottom"|Zobacz uwagi poniżej.|  
|DontForceCreate|REG_DWORD|0 lub 1|Gdy ten wpis jest dostępny i jego wartość nie jest równa zero, okna są załadowane, ale nie natychmiast wyświetlone.|  
  
### <a name="comments"></a>Komentarze  
 Wpis orientacji definiuje pozycji, gdy okno narzędzia stacje dokujące po dwukrotnym kliknięciu pasku tytułu. Pozycja jest określana względem okna określony we wpisie okna. Jeśli wpis styl jest ustawiony na "Połączonej", wpis orientacji może być "Lewo", "Prawej", "Top" lub "Bottom". Jeśli wpis stylu "Kartach" orientację wpis może być "Left" lub "Prawej" i określa, gdzie jest dodawany karcie. W przypadku wejścia styl "Float", najpierw przesunięty okna narzędzia. Po dwukrotnym kliknięciu paska tytułu Zastosuj wpisy orientację i okna, a okno używa stylu "Kartach". Jeżeli styl jest "AlwaysFloat", nie zadokowane okna narzędzia. Jeżeli styl jest "MDI", okna narzędzi jest powiązana z obszarem MDI i okno wpis zostanie zignorowany.  
  
### <a name="example"></a>Przykład  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>Widoczność okna narzędzi  
 Wartości w podkluczu widoczność Opcjonalnie określ ustawienia widoczności okna narzędzia. Nazwy wartości są używane do przechowywania identyfikatorów GUID poleceń, które wymagają widoczność okna. Jeśli polecenie zostanie wykonane, IDE gwarantuje, że okno narzędzia jest utworzony i stają się widoczne.  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|(Domyślnie)|REG_SZ|Brak|Pozostaw pole puste.|  
|*\<IDENTYFIKATOR GUID >*|REG_DWORD lub REG_SZ|0 lub ciąg opisujący.|Opcjonalny. Nazwa wejścia musi być identyfikator GUID polecenia wymagające widoczności. Wartość zawiera tylko ciąg informacyjny. Wartość jest zazwyczaj `reg_dword` równa 0.|  
  
### <a name="example"></a>Przykład  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPackages](../extensibility/internals/vspackages.md)