---
title: "Powiązanie skróty do elementów Menu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1fe1c0bb9c3028c70e1be9df9af1de3b0804844e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>Skróty klawiaturowe powiązania elementów Menu
Aby powiązać polecenia niestandardowych menu skrótów klawiaturowych, Dodaj wpis w pliku vsct dla pakietu. W tym temacie opisano sposób mapowania skrót klawiaturowy do niestandardowych przycisku, element menu lub poleceń narzędzi oraz sposób zastosować Mapowanie klawiatury w domyślnym edytorem lub ograniczenie go do edytora niestandardowego.  
  
 Aby przypisać skróty do istniejących elementów menu programu Visual Studio, zobacz [zidentyfikowanie i dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choosing-a-key-combination"></a>Wybranie kombinacji klawiszy  
 Wiele skróty klawiaturowe są już używane w programie Visual Studio. Nie należy przypisywać ten sam skrót do więcej niż jednego polecenia, ponieważ zduplikowane powiązania są trudne do wykrycia i może również spowodować nieoczekiwane wyniki. W związku z tym jest dobrym rozwiązaniem, aby sprawdzić dostępność skrót przed przypisaniem go.  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Aby zweryfikować dostępność skrótów klawiaturowych  
  
1.  W **narzędzia / Opcje / środowiska** wybierz **klawiatury**.  
  
2.  Upewnij się, że **Użyj nowego skrótu w** ustawiono **Global**.  
  
3.  W **klawiszy skrótów** wpisz skrót klawiaturowy, który ma być używany.  
  
     Jeśli skrót jest już używany w programie Visual Studio, **Shorcut aktualnie używane przez** zostanie wyświetlone polecenie, które obecnie wywołuje skrótu.  
  
4.  Spróbuj różnych kombinacji klawiszy, aż do znalezienia nie jest zamapowany.  
  
    > [!NOTE]
    >  Skróty klawiaturowe, które używają ALT może otworzyć menu i nie są bezpośrednio wykonania polecenia. W związku z tym **Shorcut aktualnie używane przez** pole może być puste podczas wpisywania skrótu klawiaturowego, który zawiera ALT. Możesz sprawdzić, czy skrót nie powoduje otwarcia menu przez zamknięcia **opcje** okno dialogowe i naciskając klawisz kluczy.  
  
 W poniższej procedurze przyjęto, że masz istniejący pakiet VSPackage za pomocą polecenia menu. Jeśli potrzebujesz pomocy, które, Przyjrzyjmy się [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Aby przypisać skrót klawiaturowy do polecenia  
  
1.  Otwórz plik vsct pakietu.  
  
2.  Utwórz pustą `<KeyBindings>` sekcji po `<Commands>` Jeśli nie jest już istnieje.  
  
    > [!WARNING]
    >  Aby uzyskać więcej informacji na temat powiązań klucza, zobacz [Keybinding](../extensibility/keybinding-element.md).  
  
     W `<KeyBindings>` sekcji, Utwórz `<KeyBinding>` wpisu.  
  
     Ustaw `guid` i `id` przyznaje polecenie do wywołania.  
  
     Ustaw `mod1` atrybutu **kontroli**, **Alt**, lub **Shift**.  
  
     W sekcji powiązań kluczy powinien wyglądać następująco:  
  
    ```xml  
    <KeyBindings>  
        <KeyBinding guid="<name of command set>" id="<name of command id>"  
            editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
    </KeyBindings>  
  
    ```  
  
 Jeśli skrót klawiaturowy wymaga więcej niż dwa klucze, ustaw `mod2` i `key2` atrybutów.  
  
 W większości przypadków **Shift** nie powinna być używana bez drugi modyfikujący, ponieważ już naciśnięcie przycisku powoduje, że większość klawiszy alfanumeryczne na typ wielką literę lub symbol.  
  
 Kody klucza wirtualne umożliwiają uzyskanie dostępu do klawisze specjalne, które nie mają znaku skojarzonych z nimi, na przykład klawiszy funkcyjnych i **BACKSPACE** klucza. Aby uzyskać więcej informacji, zobacz [kody wirtualnej klucza](http://go.microsoft.com/fwlink/?LinkID=105932).  
  
 Aby udostępnić polecenie w programie Visual Studio edytora, ustaw `editor` atrybutu `guidVSStd97`.  
  
 Aby udostępnić polecenie tylko w edytorze niestandardowe, należy ustawić `editor` atrybutu nazwy niestandardowego edytora, który został wygenerowany przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] szablon pakietu podczas tworzenia pakiet VSPackage, który zawiera Edytor niestandardowy. Aby znaleźć wartości nazwy, Szukaj w `<Symbols>` sekcji `<GuidSymbol>` węzła których `name` atrybutu kończy się na "`editorfactory`." Jest to nazwa edytora niestandardowego.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wiąże skrótu klawiaturowego CTRL + ALT + C do polecenia o nazwie `cmdidMyCommand` w pakiecie o nazwie `MyPackage`.  
  
```  
<CommandTable>  
. . .  
<Commands>  
. . .  
</Commands>  
<KeyBindings>  
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"   
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />  
</KeyBindings>  
. . .  
</CommandTable>  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wiąże skrót klawiaturowy CTL + B polecenie o nazwie `cmdidBold` w projekcie o nazwie `TestEditor`. Polecenie jest dostępne tylko w edytorze niestandardowej, a nie w innych edytory.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)