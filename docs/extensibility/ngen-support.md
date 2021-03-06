---
title: Obsługa ngen w rozszerzeniu VSIX v3 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3b5f9c7b297d98836ca3e5c017d2a0d440a30470
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495482"
---
# <a name="ngen-support-in-vsix-v3"></a>Obsługa Ngen w rozszerzeniu VSIX v3

Za pomocą programu Visual Studio 2017 i nowe rozszerzeniu VSIX v3 (wersja 3) rozszerzenia manifestu format rozszerzenia deweloperzy mogą teraz "ngen" ich zestawów w czasie instalacji.

Poniżej przedstawiono fragment MSDN, który objaśnia, jakie "ngen" jest:

>Generator obrazu natywnego (*Ngen.exe*) jest narzędziem, które poprawia wydajność zarządzanych aplikacji. *Ngen.exe* tworzy obrazy natywne, które są plikami zawierającymi skompilowany kod maszynowy dla danego procesora i instaluje je w pamięci podręcznej obrazów natywnych na komputerze lokalnym. Środowisko uruchomieniowe może używać obrazów natywnych z tej pamięci podręcznej, zamiast używać kompilatora JIT (Just-In-Time) w celu skompilowania oryginalnego zestawu.
>
>z [Ngen.exe (Generator obrazu natywnego)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Z kolei "ngen" na zestawie VSIX muszą być zainstalowane "dla wystąpienia na komputerze". Tę można włączyć, zaznaczając pole wyboru "wszystkich użytkowników" `extension.vsixmanifest` projektanta:

![Zaznacz wszystkich użytkowników](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Jak włączyć Ngen

Aby włączyć ngen w zestawie, można użyć **właściwości** okna w programie Visual Studio.

Istnieją 4 właściwości, które można ustawić:

1. **Ngen** (wartość logiczna) — w przypadku opcji true Instalatora programu Visual Studio będzie "ngen" zestawu.
2. **Aplikacja ngen** (ciąg) — Ngen daje szansę na korzystanie z aplikacji *app.config* pliku, aby można było rozpoznać zależności zestawu. Ta wartość powinna być równa aplikacji którego *app.config* chcesz użyć (względem katalogu instalacyjnego programu Visual Studio).
3. **Architektura ngen** (enum) — architektura natywnie skompilować zestawu. Opcje to:. B wartości NotSpecified. X86 c. X64 d. Wszystkie
4. **Priorytet ngen** (całkowitą z zakresu od 1 do 3) — poziom priorytetu programu Ngen jest udokumentowany na [poziomy priorytetów Ngen.exe](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels).

W tym miejscu przedstawiono **właściwości** okna w akcji:

![ngen we właściwościach](media/ngen-in-properties.png)

Spowoduje to dodanie metadanych do odwołania projektu w projekcie VSIX *.csproj* pliku:

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

 >**Uwaga:** edytować plik .csproj bezpośrednio, jeśli użytkownik sobie tego życzy.

## <a name="extra-information"></a>Dodatkowe informacje

Zmiany projektanta właściwości są stosowane do więcej niż tylko odwołania do projektu; można ustawić metadanych Ngen dla elementów wewnątrz projektu również (przy użyciu tych samych metod opisanych powyżej) tak długo, jak elementy znajdują się zestawy .NET.