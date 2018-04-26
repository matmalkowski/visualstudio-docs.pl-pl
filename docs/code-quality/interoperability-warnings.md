---
title: Współdziałanie — Ostrzeżenia
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 71f954658d12a9d2789315007668b152a9523923
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="interoperability-warnings"></a>Współdziałanie — Ostrzeżenia
Ostrzeżenia międzyoperacyjności obsługują funkcję interakcji z klientami COM.

## <a name="in-this-section"></a>W tej sekcji

|Reguła|Opis|
|----------|-----------------|
|[CA1400: Powinny istnieć punkty wejścia P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Metoda publiczna lub chroniona jest oznaczona za pomocą atrybutu System.Runtime.InteropServices.DllImportAttribute. Nie można zlokalizować biblioteki niezarządzanej lub dopasować metody do funkcji w bibliotece.|
|[CA1401: P/Invoke nie powinny być widoczne](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Metody publiczne lub chronione w typu publicznego ma atrybut elementu System.Runtime.InteropServices.DllImportAttribute (również implementowana według słów kluczowych Declare w języku Visual Basic). Takie metody nie powinny być udostępniane.|
|[CA1402: Unikaj przeciążeń w interfejsach widocznych dla modelu COM](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Gdy przeciążone metody są udostępniane klientom COM, tylko pierwsze przeciążenie metody zachowuje swoją nazwę. Kolejne przeciążenia są jednoznacznie nazywane przez dołączenie do nazwy znaku podkreślenia (_) i liczby całkowitej, która odpowiada kolejności deklaracji przeciążeń.|
|[CA1403: Typy automatycznego układu nie powinny być widoczne dla modelu COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Typ wartości widocznej dla modelu COM jest oznaczony za pomocą atrybutu System.Runtime.InteropServices.StructLayoutAttribute ustawionego na LayoutKind.Auto. Układ tego typu można zmieniać między wersjami [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], która spowoduje zerwanie klientów modelu COM, w których jest oczekiwany określony układ.|
|[Ca1404: należy Wywołać GetLastError natychmiast po P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Wywołanie do metody Marshal.GetLastWin32Error lub jego odpowiednik [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] funkcji GetLastError i natychmiast poprzedniego wywołania nie jest to platforma wywołania metody.|
|[CA1405: Typy podstawowe typu widocznego dla modelu COM powinny być widoczne dla modelu COM](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Typ widoczny dla modelu COM pochodzi od typu, który nie jest widoczny dla modelu COM.|
|[CA1406: Unikaj argumentów typu Int64 w przypadku klientów programu Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Visual Basic 6 COM klienci nie mają dostępu 64-bitowych liczb całkowitych.|
|[CA1407: Unikaj składowych statycznych w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|Model COM nie obsługuje metod statycznych.|
|[CA1408: Nie używaj wartości ClassInterfaceType dla elementu AutoDual](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|Typy, które korzystają z podwójnych interfejsów, umożliwiają klientom powiązanie z określonym interfejsem. Wszelkie zmiany w przyszłej wersji układu typu lub wszelkich typów podstawowych spowodują przerwanie klientów COM powiązanych z interfejsem. Domyślnie jeśli atrybut ClassInterfaceAttribute nie jest określony, używany jest interfejs służący tylko do wysłania.|
|[CA1409: Typy widoczne dla modelu COM powinny być możliwe do utworzenia](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Typ odwołania, który jest specjalnie oznaczony jako widoczny dla modelu COM, zawiera publiczny konstruktor sparametryzowany, ale nie zawiera publicznego domyślnego (bezparametrowego) konstruktora. Klienci COM nie mogą stworzyć typu bez publicznego konstruktora domyślnego.|
|[CA1410: Metody rejestracji modelu COM powinny być dopasowane](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Typ deklaruje metody, która jest oznaczona za pomocą <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atrybutu, ale nie deklaruje metody, która jest oznaczona za pomocą <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atrybutu, albo na odwrót.|
|[CA1411: Metody rejestracji modelu COM nie powinny być widoczne](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Metody, która jest oznaczona za pomocą atrybutu System.Runtime.InteropServices.ComRegisterFunctionAttribute lub atrybutu System.Runtime.InteropServices.ComUnregisterFunctionAttribute jest widoczne na zewnątrz.|
|[CA1412: Oznacz interfejsy ComSource jako interfejsy IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Typ jest oznaczony za pomocą atrybutu System.Runtime.InteropServices.ComSourceInterfacesAttribute i co najmniej jeden z określonych interfejsów nie jest oznaczony za pomocą atrybutu System.Runtime.InteropServices.InterfaceTypeAttribute ustawionego na ComInterfaceType.InterfaceIsIDispatch.|
|[CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Pola niepubliczne wystąpień typów wartości widocznych dla modelu COM są widoczne dla klientów COM. Przejrzyj zawartość pól pod kątem informacji, które nie powinny być eksponowane lub będą mieć niezamierzone efekty dla projektu lub zabezpieczeń.|
|[CA1414: Oznacz logiczne argumenty P/Invoke za pomocą MarshalAs](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Typ danych Boolean ma wiele reprezentacji w kodzie niezarządzanym.|
|[CA1415: Poprawnie zadeklarować P/Invoke](../code-quality/ca1415-declare-p-invokes-correctly.md)|Ta zasada szuka wywołanie platformy deklaracje metody kierowanych [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] funkcje, które mają wskaźnik do OVERLAPPED struktury parametru i odpowiadającego mu parametru zarządzanego nie jest wskaźnikiem do <xref:System.Threading.NativeOverlapped?displayProperty=fullName> struktury.|