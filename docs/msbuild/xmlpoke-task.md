---
title: Xmlpoke — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31c76ba53e858d9eab41d6579950f47b16f8c9b8
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056358"
---
# <a name="xmlpoke-task"></a>XmlPoke — Zadanie

Ustawia wartości określonych przez zapytanie XPath do pliku XML.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `XmlPoke` zadań.
  
|Parametr|Opis|
|---------------|-----------------|
|`Namespaces`|Opcjonalne `String` parametru.<br /><br /> Określa przestrzeni nazw dla prefiksów kwerendy XPath. `Namespaces` jest fragment kodu XML, składające się z `Namespace` elementy z atrybutami `Prefix` i `Uri`. Atrybut `Prefix` Określa prefiks do skojarzenia z przestrzeni nazw określonej w `Uri` atrybutu. Nie używaj pustą `Prefix`.|
|`Query`|Opcjonalne `String` parametru.<br /><br /> Określa zapytanie XPath.|
|`Value`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa wartość, która ma zostać wstawiony do określonej ścieżki.|
|`XmlInputPath`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa dane wejściowe XML jako ścieżkę pliku.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Oto sample.xml, aby zmodyfikować:

```
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" >
<Identity Name="Sample.Product " Publisher="CN=1234" Version="1.0.0.0" />
<mp:PhoneIdentity PhoneProductId="456" PhonePublisherId="0" />
</Package>
```

W tym przykładzie, jeśli chcesz zmodyfikować `/Package/mp:PhoneIdentity/PhonePublisherId`, następnie użyć

```
<Project>
  <PropertyGroup>
    <Namespace>
        <Namespace Prefix="dn" Uri="http://schemas.microsoft.com/appx/manifest/foundation/windows10" />
        <Namespace Prefix="mp" Uri="http://schemas.microsoft.com/appx/2014/phone/manifest" />
        <Namespace Prefix="uap" Uri="http://schemas.microsoft.com/appx/manifest/uap/windows10" />
    </Namespace>
</PropertyGroup>

<Target Name="Poke">
  <XmlPoke
    XmlInputPath="Sample.xml"
    Value="MyId"
    Query="/dn:Package/mp:PhoneIdentity/@PhoneProductId"
    Namespaces="$(Namespace)"/>
</Target>
</Project>
```

`dn` w tym miejscu służy jako prefiks przestrzeni nazw sztuczne dla domyślnej przestrzeni nazw.

## <a name="see-also"></a>Zobacz też

 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
