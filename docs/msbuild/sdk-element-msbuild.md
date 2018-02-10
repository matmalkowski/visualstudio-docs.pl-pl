---
title: "Zestaw SDK — Element (MSBuild) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/25/2018
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Sdk element [MSBuild]
- <Sdk> element [MSBuild]
author: jeffkl
ms.author: jeffkl
manager: angerlic
ms.workload:
- multiple
ms.openlocfilehash: e82a66835ca3b104df325009f7253fafbc429eab
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="sdk-element-msbuild"></a>Zestaw SDK — Element (MSBuild)
Odwołania [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekt zestawu SDK.  

 \<Project>  
 \<Sdk>  


## <a name="syntax"></a>Składnia  

```  
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />  
```  

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  

### <a name="attributes"></a>Atrybuty  

|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Atrybut wymagany.<br /><br /> Nazwa projektu zestawu SDK.|  
|`Version`|Atrybut opcjonalny.<br /><br /> Wersja projektu zestawu SDK|  

### <a name="child-elements"></a>Elementy podrzędne  
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne  
 |Element|Opis|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Wymaganego głównego elementu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu.|  

## <a name="see-also"></a>Zobacz też  
 [Porady: odwołania projektu MSBuild zestawu SDK](../msbuild/how-to-use-project-sdk.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)
