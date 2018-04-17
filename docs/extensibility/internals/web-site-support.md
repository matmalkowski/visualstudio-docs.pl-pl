---
title: Witryna sieci Web pomocy technicznej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d3da310c6695598eef36998cc562f6d477eff29
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="web-site-support"></a>Witryna sieci Web pomocy technicznej
System projektu witryny sieci Web to system projektu, który tworzy projekty sieci Web. Projekty sieci Web z kolei tworzenie aplikacji sieci Web. Projekt witryny sieci Web generuje jednego pliku wykonywalnego dla każdej strony sieci Web, który jest skojarzony kod. Dodatkowe pliki wykonywalne zostaną wygenerowane na podstawie plików kodu źródłowego w folderze /App_Code.  
  
 Systemy projektu witryny sieci Web są tworzone przez dodanie szablony i atrybuty rejestracji w istniejącym systemie projektu. Wybiera jeden z tych atrybutów dostawcy IntelliSense dla języka. Implementacja dostawcy IntelliSense obsługuje odwołania i wywołuje kompilatora języka zleconą inteligentne strony sieci Web, które nie są buforowane.  
  
 Kompilator języka używana do kompilowania strony sieci Web musi być zarejestrowana w [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]. Można użyć [ \<kompilatora > elementu](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) w pliku Web.config, aby zarejestrować kompilatora, jak w poniższym przykładzie:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Szablony pomocy technicznej dotyczącej witryn internetowych](../../extensibility/internals/web-site-support-templates.md)  
 Wyświetla listę szablonów, które służą do tworzenia nowych projektów witryny sieci Web i skojarzone elementy.  
  
 [Atrybuty pomocy technicznej dotyczącej witryn internetowych](../../extensibility/internals/web-site-support-attributes.md)  
 Przedstawia informacje o atrybuty rejestracji połączyć projekt witryny sieci Web, aby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)].  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Projekty internetowe](../../extensibility/internals/web-projects.md)  
 Zawiera omówienie programu dwa rodzaje projektów sieci Web, projektów witryny sieci Web i projekty aplikacji sieci Web.