---
title: "Wstążka XML | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTO.Ribbon.RibbonXMLItem
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- callback methods
- custom Ribbon, displaying
- custom Ribbon, defining behavior
- XML [Office development in Visual Studio], Ribbon
- customizing the Ribbon, defining behavior
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, displaying
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e12489431a7496b1d64d5aef93a24fcc239be81a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="ribbon-xml"></a>XML — Wstążka
  Element wstążki (XML) można dostosować za pomocą XML wstążki. Jeśli chcesz dostosować na Wstążce w taki sposób, który nie jest obsługiwany przez element wstążki (projektanta wizualnego), należy użyć elementu wstążki (XML). Porównanie co można zrobić z każdym elementem, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="adding-a-ribbon-xml-item-to-a-project"></a>Dodawanie do projektu element wstążki (XML)  
 Możesz dodać **wstążki (XML)** element do żadnego projektu pakietu Office z **Dodaj nowy element** okno dialogowe. Visual Studio automatycznie dodaje następujące pliki do projektu:  
  
-   Plik XML wstążki. Ten plik definiuje wstążki interfejsu użytkownika (UI). Użyj tego pliku, aby dodać elementy interfejsu użytkownika, takie jak karty, grupy i kontrolek. Aby uzyskać więcej informacji, zobacz [odwołanie do pliku XML wstążki](#RibbonDescriptorFile) dalszej części tego tematu.  
  
-   Plik kodu wstążki. Ten plik zawiera *wstążki klasy*. Ta klasa ma nazwę, którą określono dla **wstążki (XML)** elementu **Dodaj nowy element** okno dialogowe. Aby załadować niestandardowa Wstążka aplikacji Microsoft Office użyć wystąpienia tej klasy. Aby uzyskać więcej informacji, zobacz [odwołania do klasy wstążki](#RibbonExtensionClass) dalszej części tego tematu.  
  
 Domyślnie te pliki dodaj niestandardową grupę do **Add-Ins** kartę na Wstążce.  
  
## <a name="displaying-the-custom-ribbon-in-a-microsoft-office-application"></a>Wyświetlanie niestandardowych wstążki w aplikacji pakietu Microsoft Office  
 Po dodaniu **wstążki (XML)** elementu do projektu, należy dodać kodu **thisaddin —**, **ThisWorkbook**, lub **ThisDocument** — klasa czy zastępuje metodę CreateRibbonExtensibilityObject i zwraca klasy XML wstążki do aplikacji pakietu Office.  
  
 Poniższy przykładowy kod zastępuje metodę CreateRibbonExtensibilityObject i zwraca klasę kodu XML wstążki o nazwie MyRibbon.  
  
 [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
 [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
## <a name="defining-the-behavior-of-the-custom-ribbon"></a>Definiowanie zachowania niestandardowa Wstążka  
 Może odpowiadać na działania użytkownika, takie jak kliknięcie przycisku na Wstążce, tworząc *metody wywołania zwrotnego*. Metody wywołania zwrotnego podobne zdarzenia w formantach formularzy systemu Windows, ale są one zidentyfikowane przez atrybut w XML elementu interfejsu użytkownika. Zapisywanie metod w klasie Wstążki i formantu wywołuje metodę, która ma taką samą nazwę jak wartość atrybutu. Na przykład można utworzyć metody wywołania zwrotnego, która jest wywoływana, gdy użytkownik kliknie przycisk na Wstążce. Dwa kroki są wymagane do utworzenia metody wywołania zwrotnego:  
  
-   Atrybut przypisuje do formantu w pliku XML wstążki, który identyfikuje metodę wywołania zwrotnego w kodzie.  
  
-   Zdefiniuj metodę wywołania zwrotnego w klasie wstążki.  
  
> [!NOTE]  
>  Program Outlook wymaga dodatkowych czynności. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wstążki do programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
 Aby uzyskać wskazówki, który demonstruje sposób automatyzowania aplikacji na Wstążce, zobacz [wskazówki: tworzenie kart niestandardowych za pomocą XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md).  
  
### <a name="assigning-callback-methods-to-controls"></a>Przypisywanie metod wywołania zwrotnego do formantów  
 Aby przypisać metody wywołania zwrotnego do formantu w pliku XML wstążki, Dodaj atrybut, który określa typ metody wywołania zwrotnego i nazwę metody. Na przykład następujący element definiuje przycisk przełącznika, który ma **onAction** metody wywołania zwrotnego o nazwie `OnToggleButton1`.  
  
```  
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />  
```  
  
 **onAction** jest wywoływane, gdy użytkownik wykona głównych zadanie skojarzone z określonego formantu. Na przykład **onAction** Metoda wywołania zwrotnego przycisku przełączania jest wywoływana, gdy użytkownik kliknie przycisk.  
  
 Metoda określona w atrybucie może mieć dowolną nazwę. Jednak musi być zgodna Nazwa metody, która definiuje się w pliku kodu wstążki.  
  
 Istnieje wiele różnych typów metody wywołania zwrotnego, które można przypisać do formantów wstążki. Aby uzyskać pełną listę dostępnych metod wywołania zwrotnego dla każdego formantu, zobacz artykułu technicznego [Dostosowywanie interfejsu użytkownika wstążki pakietu Office (2007) dla deweloperów (część 3 z 3)](http://msdn.microsoft.com/en-us/a16c7df5-93f3-4920-baa8-7b7290794c15).  
  
###  <a name="CallBackMethods"></a>Definiowanie metody wywołania zwrotnego  
 Zdefiniuj metody wywołania zwrotnego w klasie wstążki w pliku kodu wstążki. Metoda wywołania zwrotnego ma kilka wymagań:  
  
-   Musi być zadeklarowany jako publiczny.  
  
-   Jego nazwa musi odpowiadać nazwie metody wywołania zwrotnego, który przypisany do formantu w pliku XML wstążki.  
  
-   Podpis musi być zgodna podpis typu metody wywołania zwrotnego, która jest dostępna dla skojarzonym formancie wstążki.  
  
 Pełną listę podpisów metody wywołania zwrotnego dla formantów wstążki, zobacz artykuł techniczne [Dostosowywanie interfejsu użytkownika wstążki pakietu Office (2007) dla deweloperów (część 3 z 3)](http://msdn.microsoft.com/en-us/a16c7df5-93f3-4920-baa8-7b7290794c15). Program Visual Studio nie zapewnia obsługę funkcji IntelliSense dla metody wywołania zwrotnego, utworzonych w pliku kodu wstążki. W przypadku utworzenia metody wywołania zwrotnego prawidłowy podpis jest niezgodny, zostanie skompilowany kod, ale nic nie zostanie przeprowadzona po kliknięciu formantu.  
  
 Wszystkie metody wywołania zwrotnego ma <xref:Microsoft.Office.Core.IRibbonControl> parametr, który reprezentuje kontrolkę, która wywołuje metodę. Ten parametr umożliwia ponowne użycie tej samej metody wywołania zwrotnego dla wielu formantów. Poniższy przykład kodu pokazuje **onAction** metody wywołania zwrotnego, który wykonuje różne zadania, w zależności od tego, które klika formant użytkownika.  
  
 [!code-csharp[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#2)]
 [!code-vb[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#2)]  
  
##  <a name="RibbonDescriptorFile"></a>Odwołanie do pliku XML wstążki  
 Można zdefiniować Twojej niestandardowa Wstążka przez dodanie elementów i atrybutów do pliku XML wstążki. Domyślnie plik XML wstążki zawiera następujący kod XML.  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<customUI xmlns="http://schemas.microsoft.com/office/2006/01/customui" onLoad="OnLoad">  
  <ribbon>  
    <tabs>  
      <tab idMso="TabAddIns">  
        <group id="MyGroup"  
               label="My Group">  
        </group>  
      </tab>  
    </tabs>  
  </ribbon>  
</customUI>  
```  
  
 W poniższej tabeli opisano elementy domyślnej w pliku XML wstążki.  
  
|Element|Opis|  
|-------------|-----------------|  
|**customUI**|Reprezentuje niestandardowa Wstążka w projekcie dodatku VSTO.|  
|**Wstążka**|Reprezentuje wstążki.|  
|**karty**|Reprezentuje zestaw karty wstążki.|  
|**Karta**|Reprezentuje pojedynczy karty wstążki.|  
|**grupy**|Reprezentuje grupę formantów na karcie wstążki.|  
  
 Tych elementów mają atrybuty, które określają wygląd i zachowanie niestandardowa Wstążka. W poniższej tabeli opisano atrybuty domyślne w pliku XML wstążki.  
  
|Atrybut|Element nadrzędny|Opis|  
|---------------|--------------------|-----------------|  
|**onLoad**|**customUI**|Określa metodę, która jest wywoływana podczas ładowania aplikacji wstążki.|  
|**idMso**|**Karta**|Identyfikuje wbudowanej karty do wyświetlenia na Wstążce.|  
|**id**|**grupy**|Identyfikuje grupę.|  
|**etykiety**|**grupy**|Określa tekst wyświetlany w grupie.|  
  
 Domyślne elementy i atrybuty w pliku XML wstążki to mały podzbiór elementów i atrybutów, które są dostępne. Aby uzyskać pełną listę dostępnych elementów i atrybutów, zobacz artykuł techniczne [Dostosowywanie interfejsu użytkownika wstążki pakietu Office (2007) dla deweloperów (część 2 z 3)](http://msdn.microsoft.com/en-us/6b904f55-525f-4520-9b81-a017db65657b).  
  
##  <a name="RibbonExtensionClass"></a>Odwołania do klasy wstążki  
 Visual Studio wygeneruje klasy wstążki w pliku kodu wstążki. Metody wywołania zwrotnego dla formantów na Wstążce należy dodać do tej klasy. Ta klasa implementuje <xref:Microsoft.Office.Core.IRibbonExtensibility> interfejsu.  
  
 W poniższej tabeli opisano metody domyślnej z tej klasy.  
  
|Metoda|Opis|  
|------------|-----------------|  
|`GetCustomUI`|Zwraca zawartość pliku XML wstążki. Aplikacje Microsoft Office wywołują tę metodę w celu uzyskania ciągu XML, który definiuje interfejs użytkownika programu niestandardowa Wstążka. Ta metoda implementuje <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> metody. **Uwaga:** `GetCustomUI` powinny być implementowane tylko do zwrócenia zawartości pliku XML wstążki; nie można stosować zainicjować dodatku VSTO programu. W szczególności nie należy wyświetlić okno dialogowe lub innych okien w Twojej `GetCustomUI` implementacji. W przeciwnym razie wartość niestandardowa Wstążka może nie działać poprawnie. Jeśli masz do uruchomienia kodu, który inicjuje użytkownika dodatku VSTO Dodaj kod, aby `ThisAddIn_Startup` obsługi zdarzeń.|  
|`OnLoad`|Przypisuje <xref:Microsoft.Office.Core.IRibbonControl> parametr `ribbon` pola. Aplikacje Microsoft Office wywołać tę metodę, gdy są ładowane niestandardowa Wstążka. To pole umożliwia dynamiczne aktualizowanie niestandardowa Wstążka. Aby uzyskać więcej informacji, zobacz artykuł techniczny [Dostosowywanie interfejsu użytkownika wstążki pakietu Office (2007) dla deweloperów (część 1 z 3)](http://msdn.microsoft.com/en-us/a4fd6d18-d4a8-4e64-bd89-f437208573d3).|  
|`GetResourceText`|Wywoływane przez `GetCustomUI` metodę, aby uzyskać zawartość pliku XML wstążki.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [Wskazówki: Tworzenie kart niestandardowych za pomocą XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)  
  
  