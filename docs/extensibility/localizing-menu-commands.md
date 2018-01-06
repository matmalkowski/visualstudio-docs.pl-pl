---
title: Lokalizowanie polecenia Menu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 77bd698149ca4e73b462fc3ada9256ba5911177e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="localizing-menu-commands"></a>Lokalizowanie poleceń Menu
Możesz podać zlokalizowany tekst menu i narzędzi poleceń, tworząc vsct zlokalizowanych plików i zlokalizowane pliki .resx dla VSPackage, a następnie zaktualizować plików projektu zmiany.  
  
 Informacje o tym, jak do zlokalizowania w procesie instalacji, zobacz [lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Lokalizowanie nazw poleceń  
 W VSPackages menu poleceń i przycisków paska narzędzi są zdefiniowane w pliku vsct.  
  
1.  W **Eksploratora rozwiązań**, Zmień nazwę pliku vsct z *filename*vsct do *filename*.en-US.vsct.  
  
2.  Utwórz kopię *filename*.en-US.vsct dla każdego zlokalizowanego języka.  
  
     Nazwy poszczególnych kopii *filename*. *Ustawienia regionalne*vsct, gdzie *ustawień regionalnych* jest nazwą określonej kultury. Aby uzyskać listę wartości nazwy kultury, zobacz [ustawień regionalnych identyfikatory przypisane przez firmę Microsoft](https://msdn.microsoft.com/en-us/library/windows/apps/jj657969.aspx).  
  
     Te *filename*. *Ustawienia regionalne*vsct pliki zawierają tekst menu zlokalizowanego pakietu.  
  
3.  Otwórz każdy *filename*. *Ustawienia regionalne*pliku vsct do zlokalizowania tekst.  
  
    1.  Modyfikowanie [ButtonText](../extensibility/buttontext-element.md) elementu wartości jako odpowiednie dla danego języka.  
  
    2.  Jeśli podasz zlokalizowanych ikony, zmodyfikuj [mapy bitowej](../extensibility/bitmap-element.md) wartości, aby wskazywał pliki docelowe.  
  
     W poniższym przykładzie przedstawiono w języku angielskim i hiszpańskim tekst przycisku polecenia otworzyć okno narzędzia Eksplorator drzewa rodziny.  
  
     [FamilyTree.en US.vsct]  
  
    ```xml  
    <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
      <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
      <Icon guid="guidImages" id="bmpPic2" />  
      <Strings>  
        <CommandName>cmdidFamilyTree</CommandName>  
        <ButtonText>Family Tree Explorer</ButtonText>  
      </Strings>  
    </Button>  
    ```  
  
     [FamilyTree.es ES.vsct]  
  
    ```xml  
    <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
      <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
      <Icon guid="guidImages" id="bmpPic2" />  
      <Strings>  
        <CommandName>cmdidFamilyTree</CommandName>  
        <ButtonText>Explorar el arbol genealogico</ButtonText>  
      </Strings>  
    </Button>  
  
    ```  
  
## <a name="localizing-other-text-resources"></a>Lokalizowanie inne zasoby tekstu  
 Zasoby tekstu innego niż nazw poleceń są definiowane w pliki zasobów (resx).  
  
1.  Zmień nazwę VSPackage.resx na VSPackage.en US.resx.  
  
2.  Utwórz kopię pliku VSPackage.en US.resx dla każdego z języków lokalizacji.  
  
     Nazwy poszczególnych kopii pakiet VSPackage. *Ustawień regionalnych*resx, gdzie *ustawień regionalnych* jest nazwą określonej kultury.  
  
3.  Zmień nazwę Resources.resx na Resources.en US.resx.  
  
4.  Utwórz kopię pliku Resources.en US.resx dla każdego z języków lokalizacji.  
  
     Nazwy poszczególnych kopii zasobów. *Ustawień regionalnych*resx, gdzie *ustawień regionalnych* jest nazwą określonej kultury.  
  
5.  Otwórz każdy plik .resx, aby zmodyfikować wartości ciągu na potrzeby określonego języka i kultury. Poniższy przykład przedstawia definicję zlokalizowanych zasobów dla pasek tytułu okna narzędzia.  
  
     [Resources.en US.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es ES.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>Dołączanie zlokalizowanych zasobów w projekcie  
 Należy zmodyfikować plik assemblyinfo.cs i plik projektu do uwzględnienia zlokalizowanych zasobów.  
  
1.  Z **właściwości** w węźle **Eksploratora rozwiązań**, otwórz assemblyinfo.cs lub assemblyinfo.vb w edytorze.  
  
2.  Dodaj następujący wpis.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     To ustawienie US English jako domyślny język.  
  
3.  Zwolnienie projektu.  
  
4.  Otwórz plik projektu w edytorze.  
  
5.  Zlokalizuj `ItemGroup` element, który zawiera `EmbeddedResource` elementów.  
  
6.  W `EmbeddedResource` Zastąp element, który wywołuje VSPackage.en-US.resx `ManifestResourceName` element z `LogicalName` element ustawioną `VSPackage.en-US.Resources`, wykonując następujące czynności.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  Dla każdego z języków lokalizacji, skopiować `EmbeddedResource` element VsPackage.en USA i zestaw **Include** atrybutu i **LogicalName** element kopii w ustawieniach regionalnych docelowym, jak pokazano w poniższym przykład.  
  
8.  Wszystkie zlokalizowane `VSCTCompile` elementu, Dodaj `ResourceName` element, który wskazuje `Menus.ctmenu`, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Zapisz plik projektu i ponownie Załaduj projekt.  
  
10. Skompiluj projekt.  
  
     Spowoduje to utworzenie głównego zestawu i zestawy zasobów dla każdego języka. Aby uzyskać informacje na lokalizowanie procesu wdrażania, zobacz [lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands Vs. OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)   
 [Globalizowanie i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)