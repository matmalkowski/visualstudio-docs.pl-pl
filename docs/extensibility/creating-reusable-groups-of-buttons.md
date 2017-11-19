---
title: "Tworzenie grup wielokrotnych przycisków | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: "44"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4be8e84c6040f3b4d57082cd39920aec2196e9f7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="creating-reusable-groups-of-buttons"></a>Tworzenie grup wielokrotnych przycisków
Grupy poleceń jest kolekcją poleceń, które zawsze występować razem w menu lub pasek narzędzi. Dowolną grupę polecenia można ponownie przypisać do menu innego elementu nadrzędnego w sekcji CommandPlacements pliku vsct.  
  
 Polecenie grupy zwykle zawierają przycisków, ale mogą także zawierać innych menu lub pola kombi.  
  
### <a name="to-create-a-reusable-group-of-buttons"></a>Aby utworzyć grupę wielokrotnych przycisków  
  
1.  Tworzenie projektu VSIX o nazwie `ReusableButtons`. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Po otwarciu projektu Dodawanie polecenia niestandardowego szablonu elementu o nazwie **ReusableCommand**. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C# / rozszerzalności** i wybierz **polecenia niestandardowych**. W **nazwa** u dołu okna, Zmień nazwę pliku polecenia, aby **ReusableCommand.cs**.  
  
3.  W pliku vsct przejdź do sekcji symboli i Znajdź element GuidSymbol, który zawiera grupy i polecenia służące do projektu. Go powinno być nazwanym guidReusableCommandPackageCmdSet.  
  
4.  Dodaj IDSymbol dla każdego przycisku, który zostanie dodany do grupy, jak w poniższym przykładzie.  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">  
        <IDSymbol name="MyMenuGroup" value="0x1020" />  
        <IDSymbol name="ReusableCommandId" value="0x0100" />  
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />  
    </GuidSymbol>  
    ```  
  
     Domyślnie szablon elementu polecenie tworzy grupę o nazwie **mojaGrupa** i ma nazwę, która została podana, wraz z IDSymbol wpis dla każdego przycisku.  
  
5.  W sekcji grupy utworzyć element grupy, który ma identyfikator GUID i identyfikator atrybuty te podane w sekcji symboli. Można również użyć istniejącej grupy lub użyj wpisu, który jest udostępniany przez polecenie szablon, jak w poniższym przykładzie. Ta grupa jest wyświetlana na **narzędzia** menu  
  
    ```xml  
    <Groups>  
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>  
        </Group>  
    </Groups>  
    ```  
  
### <a name="to-create-a-group-of-buttons-for-reuse"></a>Aby utworzyć grupę przycisków do ponownego użycia  
  
1.  Polecenia lub menu można umieścić w grupie przy użyciu grupy jako elementu nadrzędnego w definicji polecenia lub menu lub poprzez umieszczenie polecenia lub menu za pomocą sekcji CommandPlacements w grupie.  
  
     W sekcji przycisków zdefiniować przycisku, który ma grupy jako klasy nadrzędnej, lub użyj przycisku dostarczone przez szablon pakietu, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ReusableCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
2.  Jeśli przycisk musi występować w więcej niż jednej grupy, należy utworzyć wpis dla niego w sekcji CommandPlacements muszą znajdować się po sekcji poleceń. Ustawianie atrybutów identyfikator GUID i identyfikator elementu CommandPlacement na odpowiednie dla przycisku, który chcesz umieścić, a następnie ustaw identyfikator GUID i identyfikator odpowiedniego elementu nadrzędnego w stosunku do grupy docelowej, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">  
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  Wartość pola Priorytet określa pozycję polecenia w nowej grupie polecenia. Ustaw priorytetów w CommandPlacement element przesłaniają akcje w definicji elementu. Polecenia, które mają niższe wartości priorytetu są wyświetlane przed polecenia, które mają wyższe wartości priorytetu. Priorytet zduplikowane wartości są dozwolone, ale nie można zagwarantować względne położenie polecenia, które mają taką samą wartość priorytetu, ponieważ w kolejności **devenv/Setup** polecenie tworzy końcowego interfejsu z rejestru może być niespójna.  
  
### <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Aby wprowadzić wielokrotnego użytku grupy przycisków w menu.  
  
1.  Utwórz wpis w `CommandPlacements` sekcji. Ustaw identyfikator GUID i identyfikator `CommandPlacement` elementu, aby te grupy i Ustaw identyfikator GUID i identyfikator nadrzędnego do tych lokalizacji docelowej.  
  
     Powinna zostać umieszczona w sekcji CommandPlacements zaraz po sekcji poleceń:  
  
    ```xml  
    <CommandTable>  
    ...  
      <Commands>... </Commands>  
      <CommandPlacements>... </CommandPlacements>  
    ...   
    </CommandTable>  
    ```  
  
     Polecenie grupy mogą zostać włączone w menu więcej niż jeden. Menu nadrzędnego może być utworzona, jedną, która jest dostarczana przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (jak opisano w ShellCmdDef.vsct lub SharedCmdDef.vsct), lub taki, który jest zdefiniowany w innym pakiecie VSPackage. Liczba warstw element nadrzędny jest nieograniczony, pod warunkiem, menu nadrzędne ostatecznie jest podłączony do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub do menu skrótów wyświetlane przez pakiet VSPackage.  
  
     Poniższy przykład powoduje grupy na **Eksploratora rozwiązań** narzędzi z prawej strony innych przycisków.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">  
          <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    ```xml  
    <CommandPlacements>  
      <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"   
          priority="0x605">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />  
      </CommandPlacement>  
    </CommandPlacements>  
  
    ```