---
title: 'Porady: tworzenie Atom dla galerii prywatnego | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc39e4d11d826741239f11f62955fa4d2fb167cb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127480"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Porady: tworzenie Atom dla galerii prywatnych
Można utworzyć kanału Atom (RSS) do lokalizacji intranetowych, która zawiera rozszerzenia, a następnie Dodaj źródło danych do **rozszerzenia i aktualizacje** jako prywatnych galerii. Aby uzyskać więcej informacji, zobacz [galerie prywatnego](../extensibility/private-galleries.md).  
  
## <a name="creating-an-atom-feed"></a>Tworzenie Atom źródła danych  
 Można utworzyć źródła danych jako prywatnych galerii Atom, najpierw Zbierz rozszerzeń (pliki .vsix) do folderu. Można zorganizować je w podfolderach Jeśli chcesz. Należy również następujące zasoby:  
  
-   Plik atom.xml, która udostępnia jako prywatnych galerii rozszerzeń. Informacje o tym, jak połączyć pliku atom.xml do **rozszerzenia i aktualizacje**, zobacz [galerie prywatnego](../extensibility/private-galleries.md).  
  
-   Folder, który zawiera pliki obrazów, które zostały wyodrębnione z rozszerzenia (na przykład zrzuty ekranu). Plik atom.xml zawiera względne łącza do tych obrazów, tak aby były dostępne w **rozszerzenia i aktualizacje**.  
  
 Na przykład przypuśćmy, że zostaną zebrane następujące dwa rozszerzenia do folderu:  
  
-   Template_Wizard_239.vsix, który jest pusty szablon projektu VSIX.  
  
-   SelectionHighlight.vsix, które to narzędzie, aby wyróżnić wszystkie wystąpienia wybranego wyrazu.  
  
 Zawartość pliku atom.xml będą podobne do następujących:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<feed xmlns="http://www.w3.org/2005/Atom">  
<title type="text" />   
<id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
<updated>2011-04-14T21:25:48Z</updated>   
<entry>  
<id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
<title type="text">Highlight all occurrences of selected word</title>   
<summary type="text">This extends the editor to highlight ....</summary>   
<published>2011-04-14T14:24:51-07:00</published>   
<updated>2011-04-14T14:24:22-07:00</updated>   
<author>  
<name>Microsoft</name>   
</author>  
<link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />   
<link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />   
<content type="application/octet-stream" src="SelectionHighlight.vsix" />   
<Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010">  
<Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>   
<Version>1.31</Version>   
<References />   
<Rating xsi:nil="true" />   
<RatingCount xsi:nil="true" />   
<DownloadCount xsi:nil="true" />   
</Vsix>  
</entry>  
<entry>  
<id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>   
...  
</entry>  
</feed>
```  
  
 Zwróć uwagę, że tagów łącza dwóch odwołują się do zrzuty ekranu w folderze wygenerowanego obrazów.  
  
## <a name="see-also"></a>Zobacz też  
 [Galerie prywatne](../extensibility/private-galleries.md)
