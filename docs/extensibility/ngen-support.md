---
title: "Obsługa ngen w wersji 3 VSIX | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 15277f0a1038e43bb316d604cbc415da4a5d80bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ngen-support-in-vsix-v3"></a>Obsługa ngen w pliku VSIX w wersji 3

Z programu Visual Studio 2017 i nowych v3 VSIX rozszerzenia (wersja 3) manifestu format rozszerzenia deweloperzy mogą teraz "ngen" ich zestawów w czasie instalacji.

Poniżej znajduje się fragment MSDN, który objaśnia, w jaki "ngen" jest:

>Generator obrazów natywnych (Ngen.exe) jest narzędziem, które poprawia wydajność zarządzanych aplikacji. Program Ngen.exe tworzy obrazy natywne, które są plikami zawierającymi skompilowany kod maszynowy specyficzny dla procesora, i instaluje je w pamięci podręcznej obrazów natywnych na komputerze lokalnym. Środowisko uruchomieniowe może używać obrazów natywnych z tej pamięci podręcznej, zamiast używać kompilatora JIT (Just-In-Time) w celu skompilowania oryginalnego zestawu.
>
>z [Ngen.exe (Generator obrazu natywnego)](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

Z kolei "ngen" jako zestawu pliku VSIX musi być zainstalowana "poszczególnych wystąpień dla maszyny". Można je włączyć, zaznaczając pole wyboru "wszystkich użytkowników" w Projektancie extension.vsixmanifest:

![Sprawdź wszyscy użytkownicy](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Jak włączyć Ngen

Aby włączyć narzędzia ngen dla zestawów, można użyć **właściwości** okna w programie Visual Studio.

Istnieją 4 właściwości, które można ustawić:

1. **Narzędzie ngen** (wartość logiczna) — jeśli PRAWDA, Instalator programu Visual Studio będzie "ngen" zestawu.
2. **Aplikacja ngen** (ciąg) Ngen zapewnia możliwość korzystania z pliku app.config aplikacji w celu rozpoznania zależności zestawu. Ta wartość powinna być równa aplikacji app.config, którego chcesz użyć (względem katalogu instalacyjnego programu Visual Studio).
3. **Architektura ngen** (enum) — architektura natywnie skompilować używanego zestawu. Dostępne są następujące opcje:. B Płeć nieznana. X86 c. X64 d. Wszystkie
4. **Priorytet ngen** (liczba całkowita od 1 do 3) - Ngen priorytet jest udokumentowany na [poziomy priorytetu Ngen.exe](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3).

Poniżej przedstawiono informacje o **właściwości** okna w akcji:

![Narzędzie ngen we właściwościach](media/ngen-in-properties.png)

Spowoduje to dodanie metadanych odwołania projektu do wewnątrz pliku .csproj projektu VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
 ```

 >**Uwaga:** edycji pliku .csproj bezpośrednio, jeśli wolisz.

## <a name="extra-information"></a>Dodatkowe informacje

Zmiany projektanta właściwości są stosowane do więcej niż tylko odwołania do projektu; można ustawić metadane Ngen dla elementów wewnątrz projektu również (przy użyciu tych samych metod opisanych powyżej) tak długo, jak elementy będą zestawy .NET.