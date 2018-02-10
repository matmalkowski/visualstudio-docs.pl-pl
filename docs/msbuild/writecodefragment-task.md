---
title: "Writecodefragment — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6d08d4499ba0fcdc044b7189abeb9de1716b7ba4
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="writecodefragment-task"></a>WriteCodeFragment — Zadanie
Generuje plik tymczasowy kod z fragmentu określonego wygenerowanego kodu. Nie powoduje usunięcia pliku.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `WriteCodeFragment` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AssemblyAttributes`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Opis atrybutów do zapisu. Element `Include` wartość jest pełna nazwa typu atrybutu, na przykład "System.AssemblyVersionAttribute".<br /><br /> Metadane każdej to pary nazwa wartość parametru musi być typu `String`. Niektóre atrybuty umożliwiają tylko argumenty pozycyjne konstruktora. Można jednak użyć tych argumentów, w dowolny atrybut. Aby ustawić pozycyjnych konstruktora atrybutów, użyj nazwy metadanych, które przypominają "_Parameter1", "_Parameter2" i tak dalej.<br /><br /> Indeks parametru nie może być pominięte.|  
|`Language`|Wymagane `String` parametru.<br /><br /> Określa język kodu do wygenerowania.<br /><br /> `Language`mogą być dowolnego języka, dla którego dostawcy CodeDom jest dostępna, na przykład "C#" lub "VisualBasic". Emitowany plik będzie miał domyślne rozszerzenie nazwy pliku dla tego języka.|  
|`OutputDirectory`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa folder docelowy dla wygenerowanego kodu, zwykle pośredniego folderu.|  
|`OutputFile`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru wyjściowego.<br /><br /> Określa ścieżkę pliku, który został wygenerowany. Jeśli ten parametr ma wartość przy użyciu nazwy pliku, folder docelowy jest dołączany na początku nazwy pliku. Jeśli jest ustawiona przy użyciu głównego, folder docelowy jest ignorowana.<br /><br /> Jeśli ten parametr nie jest ustawiona, nazwa pliku wyjściowego jest folder docelowy, nazwa pliku dowolnego i domyślne rozszerzenie nazwy pliku w tym języku.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)