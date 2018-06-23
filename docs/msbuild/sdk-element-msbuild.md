---
title: Zestaw SDK — Element (MSBuild) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/25/2018
ms.technology: msbuild
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3d674e7613898816f905e0d0a11bdc2484cf4f25
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325326"
---
# <a name="sdk-element-msbuild"></a>Sdk — Element (MSBuild)
Odwołania [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekt zestawu SDK.  

 \<Project>  
 \<Sdk>  


## <a name="syntax"></a>Składnia  

```xml  
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
