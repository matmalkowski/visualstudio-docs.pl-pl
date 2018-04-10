---
title: SGen Task | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SGen
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SGen task [MSBuild]
- MSBuild, SGen task
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
caps.latest.revision: 11
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 95b91be303f4a4e37838e86d701e56d81e0a236a
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="sgen-task"></a>SGen — Zadanie
Tworzy zestaw serializacji XML dla typów w określonym zestawie. To zadanie zawijania narzędzie generowania serializatora XML (Sgen.exe). Aby uzyskać więcej informacji, zobacz [narzędzie generowania serializatora XML (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `SGen` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`BuildAssemblyName`|Wymagane `String` parametru.<br /><br /> Zestaw do generowania kodu serializacji dla.|  
|`BuildAssemblyPath`|Wymagane `String` parametru.<br /><br /> Ścieżka do zestawu do generowania kodu serializacji dla.|  
|`DelaySign`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, określa, czy zestawem całkowicie podpisane. Jeśli `false`, określa, że chcesz umieścić klucz publiczny w zestawie.<br /><br /> Ten parametr nie obowiązuje, chyba że używana w trybie `KeyFile` lub `KeyContainer` parametru.|  
|`KeyContainer`|Opcjonalne `String` parametru.<br /><br /> Określa kontener zawierający parę kluczy. Spowoduje to wylogowanie zestawu wstawiając klucz publiczny w manifeście zestawu. Zadanie będzie Zaloguj się w zestawie końcowym z kluczem prywatnym.|  
|`KeyFile`|Opcjonalne `String` parametru.<br /><br /> Określa pary kluczy lub klucza publicznego do użycia, aby podpisać zestaw. Kompilator wstawia klucz publiczny w manifeście zestawu, a następnie podpisuje ostateczny zestaw przy użyciu klucza prywatnego.|  
|`Platform`|Opcjonalne `String` parametru.<br /><br /> Pobiera lub ustawia platformy kompilatora służący do generowania zestawu wyjściowego. Ten parametr może mieć wartość `x86`, `x64`, lub `anycpu`. Wartość domyślna to `anycpu`.|  
|`References`|Opcjonalne `String[]` parametru.<br /><br /> Określa zestawy, które są określone przez typy wymagające serializacji XML.|  
|`SdkToolsPath`|Opcjonalne `String` parametru.<br /><br /> Określa ścieżkę do narzędzia zestawu SDK, takich jak resgen.exe.|  
|`SerializationAssembly`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Zawiera zestaw wygenerowanego serializacji.|  
|`SerializationAssemblyName`|Opcjonalne `String` parametru.<br /><br /> Określa nazwę zestawu wygenerowanego serializacji.|  
|`ShouldGenerateSerializer`|Wymagane `Boolean` parametru.<br /><br /> Jeśli `true`, zadania SGen powinien wygenerować zestawu serializacji.|  
|`Timeout`|Opcjonalne `Int32` parametru.<br /><br /> Określa ilość czasu, w milisekundach, po których plik wykonywalny zadania zostanie zakończony. Wartość domyślna to `Int.MaxValue`, wskazując, że to nie okres limitu czasu.|  
|`ToolPath`|Opcjonalne `String` parametru.<br /><br /> Określa lokalizację, z której zadanie zostanie załadowany podstawowy plik wykonywalny (sgen.exe). Jeśli ten parametr nie jest określony, zadanie użyje ścieżki instalacji zestawu SDK, odpowiadający wersji framework, na którym działa [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`Types`|Opcjonalne `String[]` parametru.<br /><br /> Pobiera lub ustawia listę określonych typów do generowania kodu serializacji dla. SGen — spowoduje wygenerowanie kodu serializacji tylko w przypadku tych typów.|  
|`UseProxyTypes`|Wymagane `Boolean` parametru.<br /><br /> Jeśli `true`, zadania SGen generuje kod serializacji tylko dla typów serwera proxy usług XML sieci Web.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.ToolTaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [tooltaskextension — klasa podstawowa](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)