---
title: "Resolvecomreference — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveCOMReference task
- ResolveCOMReference task [MSBuild]
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 07381c84ec7213fe17aabb1db91cc1ab3be6188d
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="resolvecomreference-task"></a>ResolveComReference — Zadanie
Przyjmuje listę nazw bibliotek typu lub .tlb — pliki i usuwa te biblioteki typów do lokalizacji na dysku.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `ResolveCOMReference` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`DelaySign`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, umieszcza klucz publiczny w zestawie. Jeśli `false`, pełni podpisuje zestawu.|  
|`EnvironmentVariables`|Opcjonalne `String[]` parametru.<br /><br /> Tablica par zmiennych środowiskowych, oddzielonych znaku równości. Te zmienne są przekazywane do uruchomionego tlbimp.exe i aximp.exe oprócz lub selektywnie zastępowanie, blokowanie regularne środowiska...|  
|`ExecuteAsTool`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, uruchamia tlbimp.exe i aximp.exe z odpowiedniego docelowego framework poza procesem do generowania otoki niezbędne zestawy. Ten parametr umożliwia wielowersyjności kodu.|  
|`IncludeVersionInInteropName`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, wersja biblioteki typów będą uwzględniane w nazwie otoki. Wartość domyślna to `false`.|  
|`KeyContainer`|Opcjonalne `String` parametru.<br /><br /> Określa kontener, który zawiera publiczny/prywatny<br /><br /> pary kluczy.|  
|`KeyFile`|Opcjonalne `String` parametru.<br /><br /> Określa element, który zawiera publicznego i prywatnego<br /><br /> pary kluczy.|  
|`NoClassMembers`|Opcjonalne `Boolean`parametru.|  
|`ResolvedAssemblyReferences`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Określa odwołania rozpoznanego zestawu.|  
|`ResolvedFiles`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Określa pełną pliki na dysku, które odpowiadają lokalizacje fizyczne bibliotek typów, które zostały podane jako dane wejściowe dla tego zadania.|  
|`ResolvedModules`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]`parametru.|  
|`SdkToolsPath`|Opcjonalne <xref:System.String?displayProperty=fullName> parametru.<br /><br /> Jeśli `ExecuteAsTool` jest `true`, ten parametr musi być ustawiony na ścieżkę narzędzia zestawu SDK dla framework w wersji docelowej.|  
|`StateFile`|Opcjonalne `String` parametru.<br /><br /> Określa plik pamięci podręcznej sygnatur czasowych składnika COM. Jeśli nie istnieje, uruchom co spowoduje ponowne wygenerowanie wszystkich otoki.|  
|`TargetFrameworkVersion`|Opcjonalne `String` parametru.<br /><br /> Określa wersję platformy docelowej projektu.<br /><br /> Wartość domyślna to `String.Empty`. co oznacza, że nie bez filtrowania dla odwołania oparte na platformie docelowej.|  
|`TargetProcessorArchitecture`|Opcjonalne `String` parametru.<br /><br /> Określa preferowany docelowej architektury procesora. Przekazany do flagi/Machine tlbimp.exe po translacji.<br /><br /> Wartość parametru musi być członkiem <xref:Microsoft.Build.Utilities.ProcessorArchitecture>.|  
|`TypeLibFiles`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa ścieżkę pliku biblioteki typów odwołań COM. Elementy zawarte w tym parametrze może zawierać metadane elementu. Aby uzyskać więcej informacji zobacz sekcję "TypeLibFiles metadanych elementu" poniżej.|  
|`TypeLibNames`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa nazwy biblioteki typów, aby rozwiązać. Elementy zawarte w tym parametrze musi zawierać niektóre metadane elementu. Aby uzyskać więcej informacji zobacz sekcję "TypeLibNames metadanych elementu" poniżej.|  
|`WrapperOutputDirectory`|Opcjonalne `String` parametru.<br /><br /> Lokalizacji na dysku, w którym znajduje się zestaw międzyoperacyjny wygenerowany. Jeśli ten element metadanych nie jest określona, zadanie używa ścieżkę bezwzględną katalogu którym znajduje się plik projektu.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="typelibnames-item-metadata"></a>Metadane elementu TypeLibNames  
 W poniższej tabeli opisano dostępne metadane elementu dla elementów przekazanego do `TypeLibNames` parametru.  
  
|Metadane|Opis|  
|--------------|-----------------|  
|`GUID`|Wymagany element metadanych.<br /><br /> Identyfikator GUID dla biblioteki typów. Ten element metadanych nie jest określona, zadanie nie powiedzie się.|  
|`VersionMajor`|Wymagany element metadanych.<br /><br /> Wersja główna biblioteki typów. Ten element metadanych nie jest określona, zadanie nie powiedzie się.|  
|`VersionMinor`|Wymagany element metadanych.<br /><br /> Wersja pomocnicza biblioteki typów. Ten element metadanych nie jest określona, zadanie nie powiedzie się.|  
|`LocaleIdentifier`|Opcjonalny element metadanych.<br /><br /> Identyfikator ustawień regionalnych (lub identyfikator LCID) dla biblioteki typów. Podany jako wartość 32-bitowego, która identyfikuje człowieka język preferowany przez użytkownika, regionu lub aplikacji. Jeśli ten element metadanych nie jest określona, zadanie używa domyślny identyfikator ustawień regionalnych "0".|  
|`WrapperTool`|Opcjonalny element metadanych.<br /><br /> Określa narzędzie otoki, który służy do generowania otoki zestawu dla tego typu biblioteki. Jeśli ten element metadanych nie jest określona, zadanie korzysta z domyślnym narzędziem otoki z "tlbimp". Są dostępne, bez uwzględniania wielkości liter wyboru typelibs:<br /><br /> -   `Primary`: Użyj tego narzędzia otoki, jeśli chcesz użyć już wygenerowany podstawowego zestawu międzyoperacyjnego dla składnika modelu COM. Korzystając z tego narzędzia otoki, nie należy określać katalog wyjściowy otoki ponieważ który spowoduje niepowodzenie wykonania zadania.<br />-   `TLBImp`: Użyj tego narzędzia otoki, gdy chcesz wygenerować zestawu międzyoperacyjnego dla składnika modelu COM.<br />-   `AXImp`: Użyj tego narzędzia otoki, gdy chcesz wygenerować zestawu międzyoperacyjnego dla formantu ActiveX.|  
  
## <a name="typelibfiles-item-metadata"></a>TypeLibFiles Item Metadata  
 W poniższej tabeli opisano dostępne metadane elementu dla elementów przekazanego do `TypeLibFiles` parametru.  
  
|Metadane|Opis|  
|--------------|-----------------|  
|`WrapperTool`|Opcjonalny element metadanych.<br /><br /> Określa narzędzie otoki, który służy do generowania otoki zestawu dla tego typu biblioteki. Jeśli ten element metadanych nie jest określona, zadanie korzysta z domyślnym narzędziem otoki z "tlbimp". Są dostępne, bez uwzględniania wielkości liter wyboru typelibs:<br /><br /> -   `Primary`: Użyj tego narzędzia otoki, jeśli chcesz użyć już wygenerowany podstawowego zestawu międzyoperacyjnego dla składnika modelu COM. Korzystając z tego narzędzia otoki, nie należy określać katalog wyjściowy otoki ponieważ który spowoduje niepowodzenie wykonania zadania.<br />-   `TLBImp`: Użyj tego narzędzia otoki, gdy chcesz wygenerować zestawu międzyoperacyjnego dla składnika modelu COM.<br />-   `AXImp`: Użyj tego narzędzia otoki, gdy chcesz wygenerować zestawu międzyoperacyjnego dla formantu ActiveX.|  
  
> [!NOTE]
>  Więcej informacji, które zapewniają do unikatowego identyfikowania biblioteki typów, tym większa możliwość, że zadanie rozwiąże właściwy plik na dysku.  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [klasa podstawowa zadania](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)