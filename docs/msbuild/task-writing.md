---
title: Zadanie zapisu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03c08fcc8baa0e892678cc376056a35c0f09101f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="task-writing"></a>Wpisywanie zadania
Zadania Podaj kod uruchamiany podczas procesu kompilacji. Zadania są zawarte w elementów docelowych. Biblioteka typowych zadań jest dołączana do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], i można również tworzyć własne zadania. Aby uzyskać więcej informacji na temat biblioteki zadań, które są dołączone do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], zobacz [odwołanie do zadania](../msbuild/msbuild-task-reference.md).  
  
## <a name="tasks"></a>Zadania  
 Przykłady zadań [kopiowania](../msbuild/copy-task.md), który kopiuje jeden lub więcej plików, [makedir —](../msbuild/makedir-task.md), która tworzy katalog, i [Csc](../msbuild/csc-task.md), który kompiluje [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] plików kodu źródłowego. Każde zadanie jest zaimplementowany jako klasy .NET, który implementuje <xref:Microsoft.Build.Framework.ITask> interfejs, który jest zdefiniowany w zestawie Microsoft.Build.Framework.dll.  
  
 Istnieją dwie metody, których można użyć podczas wykonywania zadania:  
  
-   Implementowanie <xref:Microsoft.Build.Framework.ITask> interfejsu bezpośrednio.  
  
-   Klasy być pochodną klasy Pomocnika <xref:Microsoft.Build.Utilities.Task>, który jest zdefiniowany w zestawie Microsoft.Build.Utilities.dll. Zadanie implementuje ITask i zawiera domyślne implementacje niektóre elementy ITask. Ponadto rejestrowanie jest łatwiejsze.  
  
 W obu przypadkach należy dodać do własnej klasy metodę o nazwie `Execute`, która jest metoda wywoływana, gdy to zadanie jest uruchamiane. Ta metoda nie przyjmuje żadnych parametrów i zwraca `Boolean` wartość: `true` Jeśli zadanie zakończyło się pomyślnie lub `false` Jeśli go nie powiodła się. W poniższym przykładzie przedstawiono zadania, które nie wykonuje żadnej akcji i zwraca `true`.  
  
```csharp
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
        }  
    }  
}  
```  
  
 Następujący plik projektu uruchomienia tego zadania:  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 Uruchomienie zadania one może również odbierać dane wejściowe z pliku projektu w przypadku utworzenia właściwości platformy .NET dla klasy zadania. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Ustawia właściwości bezpośrednio przed wywołaniem zadania `Execute` metody. Aby utworzyć właściwości ciągu, użyj kodu zadań takich jak:  
  
```csharp
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
         }  
  
        private string myProperty;  
        public string MyProperty  
        {  
            get { return myProperty; }  
            set { myProperty = value; }  
        }  
    }  
}  
```  
  
 Następujące tego zadania i zestawy uruchomień pliku projektu `MyProperty` podanej wartości:  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## <a name="registering-tasks"></a>Rejestrowanie zadania  
 Jeśli projekt będzie uruchomić zadanie, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] musi wiedzieć, jak można zlokalizować zestawu, który zawiera klasę zadań. Zadania są rejestrowane przy użyciu [usingtask — Element (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Pliku Microsoft.Common.Tasks to plik projektu, który zawiera listę `UsingTask` elementy, które rejestrują wszystkie zadania, które są dostarczane z [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Ten plik jest automatycznie dołączane podczas tworzenia każdego projektu. Jeśli zadanie, które jest zarejestrowane w Microsoft.Common.Tasks również jest zarejestrowany w bieżącym pliku projektu, bieżący plik projektu ma pierwszeństwo przed; oznacza to można zastąpić domyślne zadania z własnych zadań, który ma taką samą nazwę.  
  
> [!TIP]
>  Można wyświetlić listę zadań, które są dostarczane z [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wyświetlając zawartość Microsoft.Common.Tasks.  
  
## <a name="raising-events-from-a-task"></a>Wywoływanie zdarzeń z zadania  
 Jeśli zadanie pochodzi od <xref:Microsoft.Build.Utilities.Task> Klasa pomocy, możesz użyć dowolnej z następujących metod pomocnika w <xref:Microsoft.Build.Utilities.Task> klasy, aby wywołać zdarzenia, które zostanie przechwycony i wyświetlane przez dowolnego rejestratorów zarejestrowanych:  
  
```csharp
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Jeśli zadanie implementuje <xref:Microsoft.Build.Framework.ITask> bezpośrednio, nadal może wywoływać takie zdarzenia, ale należy użyć interfejsu IBuildEngine. W poniższym przykładzie przedstawiono zadania, który implementuje ITask i zgłasza zdarzenie niestandardowe:  
  
```csharp
public class SimpleTask : ITask  
{  
    private IBuildEngine buildEngine;  
    public IBuildEngine BuildEngine  
    {  
        get{ return buildEngine; }  
        set{ buildEngine = value; }  
    }  
  
    public override bool Execute()  
    {  
        TaskEventArgs taskEvent =  
            new TaskEventArgs(BuildEventCategory.Custom,  
            BuildEventImportance.High, "Important Message",  
           "SimpleTask");  
        BuildEngine.LogBuildEvent(taskEvent);  
        return true;  
    }  
}  
```  
  
## <a name="requiring-task-parameters-to-be-set"></a>Parametry zadania należy ustawić wymaganie  
 Niektóre właściwości zadania jako "required" można oznaczyć tak, aby ustawić wartości tych właściwości każdego pliku projektu, który uruchamia zadanie lub kompilacja zakończy się niepowodzeniem. Zastosuj `[Required]` atrybutu właściwości platformy .NET w zadania w następujący sposób:  
  
```csharp
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 `[Required]` Atrybutu jest definiowana za pomocą <xref:Microsoft.Build.Framework.RequiredAttribute> w <xref:Microsoft.Build.Framework> przestrzeni nazw.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższej [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] klasy przedstawiono zadania pochodny <xref:Microsoft.Build.Utilities.Task> Klasa pomocy. To zadanie zwraca `true`, co oznacza, że jego powodzenia.  
  
### <a name="code"></a>Kod  
  
```csharp
using System;  
using Microsoft.Build.Utilities;  
  
namespace SimpleTask1  
{  
    public class SimpleTask1: Task  
    {  
        public override bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższej [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] klasy pokazuje wykonania zadań <xref:Microsoft.Build.Framework.ITask> interfejsu. To zadanie zwraca `true`, co oznacza, że jego powodzenia.  
  
### <a name="code"></a>Kod  
  
```csharp
using System;  
using Microsoft.Build.Framework;  
  
namespace SimpleTask2  
{  
    public class SimpleTask2: ITask  
    {  
        //When implementing the ITask interface, it is necessary to  
        //implement a BuildEngine property of type  
        //Microsoft.Build.Framework.IBuildEngine. This is done for  
        //you if you derive from the Task class.  
        private IBuildEngine buildEngine;  
        public IBuildEngine BuildEngine  
        {  
            get  
            {  
                return buildEngine;  
            }  
            set  
            {  
                buildEngine = value;  
            }  
         }  
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type Object.  
        // This is done for you if you derive from the Task class.  
        private Object hostObject;  
        public Object HostObject  
        {  
            get  
            {  
                return hostObject;  
            }  
  
            set  
            {  
                hostObject = value;  
            }  
        }  
  
        public bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 To [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] pokazuje, zadań, która jest pochodną klasy <xref:Microsoft.Build.Utilities.Task> Klasa pomocy. Ma właściwość ciąg wymaganych i zgłasza zdarzenie, wyświetlane przez wszystkich rejestratorów zarejestrowanych.  
  
### <a name="code"></a>Kod  
 [!code-csharp[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład przedstawia wywoływanie poprzednie zadanie przykład SimpleTask3 pliku projektu.  
  
### <a name="code"></a>Kod  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)