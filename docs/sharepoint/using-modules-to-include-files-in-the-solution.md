---
title: "Przy użyciu modułów podczas dołączania plików rozwiązania | Dokumentacja firmy Microsoft"
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
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
ms.assetid: 74d1d69f-5cd9-452f-8d35-e1f4d8a084fd
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 484ae234839876922b6c04767d67ed56f85a108d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="using-modules-to-include-files-in-the-solution"></a>Stosowanie z modułów podczas dołączania plików do rozwiązania
  Może to być razy podczas warto wdrożyć pliki do serwera programu SharePoint, niezależnie od ich typ plików, takich jak nowe strony wzorcowej. Aby to zrobić, można użyć *modułów* (nie należy mylić z [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] modułów kodu). Moduły są kontenerami dla plików rozwiązania programu SharePoint. Po wdrożeniu rozwiązania pliki w module są kopiowane do określonych folderów na serwerze programu SharePoint.  
  
## <a name="module-items-and-elements"></a>Moduł elementów i elementy  
 Aby utworzyć moduł, dodaj go do projektu, wybierając w **Dodaj nowy element** okno dialogowe. Następnie należy zmodyfikować jego pliku Elements.xml, aby uwzględnić nazwy plików, które chcesz wdrożyć, gdzie znajdują się w systemie, a powinien zostać skopiowany na serwerze programu SharePoint.  
  
 Oto przykładowy plik Elements.xml modułu:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
    <Module Name="Module1">  
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />  
    </Module>  
</Elements>  
  
```  
  
 Nowo utworzona moduły zawierają następujące domyślne pliki:  
  
|Nazwa pliku|Opis|  
|---------------|-----------------|  
|Elements.XML|Plik definicji modułu.|  
|Przykład.txt|Plik symbolu zastępczego, który służy jako przykład pliku w module.|  
  
 Plik Elements.xml zawiera następujące elementy:  
  
|Nazwa elementu|Opis|  
|------------------|-----------------|  
|Elementy|Zawiera wszystkie elementy zdefiniowane w module.|  
|Moduł|Element modułu ma jeden atrybut *nazwa*, który określa nazwę modułu w formacie `<Module Name="Module1">`.<br /><br /> Należy pamiętać, że jeśli zmienisz nazwę modułu (lub jej *nazwa folderu* właściwości), należy ręcznie zaktualizować nazwy w elemencie modułu.<br /><br /> Jeśli określisz podkatalogu dla plików w elemencie modułu [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) automatycznie utworzy pasującego struktury katalogów dla nich.|  
|Plik|Element plików ma dwa parametry *ścieżki* i *adres Url*.<br /><br /> -Path: Nazwa i lokalizacja pliku rozwiązania programu SharePoint. Ten format jest, `Path="Module1\Sample.txt"`.<br /><br /> — Adres Url: Lokalizacja wdrożonym pliku na serwerze programu SharePoint. Ten format jest, `Url="Module1/Sample.txt"`.<br /><br /> -Type: Opcjonalny atrybut, który ma dwa ustawienia: *GhostableInLibrary* i *Ghostable*. Ten format jest, `Type="GhostableInLibrary"`. Określanie *GhostableInLibrary* oznacza, że plik zostanie dodany do biblioteki dokumentów programu SharePoint oraz elementu listy, aby dołączyć plik, gdy jest ona dodawana do biblioteki. Określanie *Ghostable* powoduje, że plik ma zostać dodany do programu SharePoint poza bibliotekę dokumentów.|  
  
 Każdego pliku, który chcesz wdrożyć wymaga oddzielnej `<File>` element wpisu w Elements.xml.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: dołączanie plików za pomocą modułu](../sharepoint/how-to-include-files-by-using-a-module.md)   
 [porady: udostępnianie pliku](http://go.microsoft.com/fwlink/?LinkID=144271)   
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Tworzenie składników Web Part dla SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  