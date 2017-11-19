---
title: Metadane dobrze znanego elementu MSBuild | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
caps.latest.revision: "12"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: dd9e082834af6194b84c7975e4a42337d66a429a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-well-known-item-metadata"></a>Metadane dobrze znanego elementu MSBuild
W poniższej tabeli opisano metadanych przypisany do każdego elementu po jego utworzeniu. W każdym przykładzie użyto następujących deklaracji elementu można dołączyć plik `C:\MyProject\Source\Program.cs` w projekcie.  
  
```xml  
<ItemGroup>  
    <MyItem Include="Source\Program.cs" />  
</ItemGroup>  
```  
  
|Metadane elementu|Opis|  
|-------------------|-----------------|  
|%(FullPath)|Zawiera pełną ścieżkę elementu. Na przykład:<br /><br /> `C:\MyProject\Source\Program.cs`|  
|%(RootDir)|Zawiera katalog główny elementu. Na przykład:<br /><br /> `C:\`|  
|%(Filename)|Zawiera nazwę pliku bez rozszerzenia elementu. Na przykład:<br /><br /> `Program`|  
|%(Extension)|Zawiera rozszerzenie nazwy pliku elementu. Na przykład:<br /><br /> `.cs`|  
|%(RelativeDir)|Zawiera ścieżkę określone w `Include` atrybut do końcowego ukośnika odwrotnego (\\). Na przykład:<br /><br /> `Source\`|  
|%(Directory)|Zawiera katalog elementu bez katalogu głównego. Na przykład:<br /><br /> `MyProject\Source\`|  
|%(RecursiveDir)|Jeśli `Include` atrybut zawiera symbol wieloznaczny \* \*, te metadane określa część ścieżki, który zastępuje symbol wieloznaczny. Aby uzyskać więcej informacji dotyczących symboli wieloznacznych, zobacz [porady: Wybieranie plików do kompilacji](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Jeśli folder *C:\MySolution\MyProject\Source\\*  zawiera plik Program.cs, a jeśli plik projektu zawiera tego elementu:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> wartość `%(MyItem.RecursiveDir)` będzie *MySolution\MyProject\Source\\*.|  
|%(Identity)|Element określony w `Include` atrybutu. Na przykład:<br /><br /> `Source\Program.cs`|  
|%(ModifiedTime)|Zawiera sygnaturę czasową, od czasu ostatniej modyfikacji elementu. Na przykład:<br /><br /> `2004-07-01 00:21:31.5073316`|  
|%(CreatedTime)|Zawiera sygnaturę czasową, od utworzenia elementu. Na przykład:<br /><br /> `2004-06-25 09:26:45.8237425`|  
|%(AccessedTime)|Zawiera sygnaturę czasową, od czasu ostatniego dostępu do niego element.<br /><br /> `2004-08-14 16:52:36.3168743`|  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy](../msbuild/msbuild-items.md)   
 [Przetwarzanie wsadowe](../msbuild/msbuild-batching.md)   
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)