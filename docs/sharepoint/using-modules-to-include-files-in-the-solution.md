---
title: Przy użyciu modułów podczas dołączania plików rozwiązania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f0773d9c167a0a799b7d9bc8ddd2b52afc9bc6f2
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120303"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Użyj modułów podczas dołączania plików rozwiązania
  Może to być razy podczas warto wdrożyć pliki do serwera programu SharePoint, niezależnie od ich typ plików, takich jak nowe strony wzorcowej. Aby to zrobić, można użyć *modułów* (nie należy mylić z [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] modułów kodu). Moduły są kontenerami dla plików rozwiązania programu SharePoint. Po wdrożeniu rozwiązania pliki w module są kopiowane do określonych folderów na serwerze programu SharePoint.  
  
## <a name="module-items-and-elements"></a>Moduł elementów i elementy
 Aby utworzyć moduł, dodaj go do projektu, wybierając w **Dodaj nowy element** okno dialogowe. Następnie należy zmodyfikować jego *Elements.xml* pliku, aby uwzględnić nazwy plików, którą chcesz wdrożyć, gdzie znajdują się w systemie, a powinien zostać skopiowany na serwerze programu SharePoint.  
  
 Oto przykład *Elements.xml* plik modułu:  
  
```xml  
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
|*Elements.XML*|Plik definicji modułu.|  
|*Przykład.txt*|Plik symbolu zastępczego, który służy jako przykład pliku w module.|  
  
 *Elements.xml* pliku zawiera następujące elementy:  
  
|Nazwa elementu|Opis|  
|------------------|-----------------|  
|Elementy|Zawiera wszystkie elementy zdefiniowane w module.|  
|Moduł|Element modułu ma jeden atrybut *nazwa*, który określa nazwę modułu w formacie `<Module Name="Module1">`.<br /><br /> Należy pamiętać, że jeśli zmienisz nazwę modułu (lub jej *nazwa folderu* właściwości), należy ręcznie zaktualizować nazwy w elemencie modułu.<br /><br /> Jeśli określisz podkatalogu dla plików w elemencie modułu [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) automatycznie utworzy pasującego struktury katalogów dla nich.|  
|Plik|Element plików ma dwa parametry *ścieżki* i *adres Url*.<br /><br /> -Path: Nazwa i lokalizacja pliku rozwiązania programu SharePoint. Ten format jest, `Path="Module1\Sample.txt"`.<br /><br /> — Adres Url: Lokalizacja wdrożonym pliku na serwerze programu SharePoint. Ten format jest, `Url="Module1/Sample.txt"`.<br /><br /> -Type: Opcjonalny atrybut, który ma dwa ustawienia: *GhostableInLibrary* i *Ghostable*. Ten format jest, `Type="GhostableInLibrary"`. Określanie *GhostableInLibrary* oznacza, że plik zostanie dodany do biblioteki dokumentów programu SharePoint oraz elementu listy, aby dołączyć plik, gdy jest ona dodawana do biblioteki. Określanie *Ghostable* powoduje, że plik ma zostać dodany do programu SharePoint poza bibliotekę dokumentów.|  
  
 Każdego pliku, który chcesz wdrożyć wymaga oddzielnej `<File>` element wpisu w *Elements.xml*.  
  
## <a name="see-also"></a>Zobacz także
 [Porady: dołączanie plików za pomocą modułu](../sharepoint/how-to-include-files-by-using-a-module.md)   
 [porady: udostępnianie pliku](http://go.microsoft.com/fwlink/?LinkID=144271)   
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Tworzenie składników web Part dla SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Pakiet i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
