---
title: "CA1060: Przenieś P-wywołuje do klasy NativeMethods | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bb93a44eebd9380499394c612ee12c40d0c62271
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: Przenieś P/Invokes do klasy NativeMethods
|||  
|-|-|  
|TypeName|MovePInvokesToNativeMethodsClass|  
|CheckId|CA1060|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Metoda używa usług wywołania platformy dostęp do niezarządzanego kodu i nie jest członkiem jednej z **NativeMethods** klasy.  
  
## <a name="rule-description"></a>Opis reguły  
 Metody wywołania platformy, takie jak te, które są oznaczone za pomocą <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atrybutu lub metody, które są zdefiniowane przy użyciu `Declare` — słowo kluczowe w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], dostęp do kodu niezarządzanego. Te metody powinny być w jednym z następujących klas:  
  
-   **NativeMethods** -tej klasy nie odrzuca przeszukiwań stosu dla uprawnień kodu niezarządzanego. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> nie może być stosowane do tej klasy.) Ta klasa jest dla metod, które mogą być używane wszędzie, ponieważ przeszukiwania stosu zostanie wykonane.  
  
-   **SafeNativeMethods** -tej klasy pomija przeszukiwań stosu dla uprawnień kodu niezarządzanego. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> jest stosowany do tej klasy.) Ta klasa jest dla metod, które są bezpieczne dla wszystkich do wywoływania. Wywołań metody te nie są wymagane do przeprowadzenia przeglądu pełne zabezpieczenia, aby upewnić się, że użycie jest bezpieczne, ponieważ metody jest bezpieczna dla każdego obiektu wywołującego.  
  
-   **UnsafeNativeMethods** -tej klasy pomija przeszukiwań stosu dla uprawnień kodu niezarządzanego. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> jest stosowany do tej klasy.) Ta klasa jest dla metod, które są potencjalnie niebezpieczne. Wywołujący dowolnego z tych metod musi wykonywanie przeglądu zabezpieczeń Pełne aby upewnić się, że użycie jest bezpieczne, ponieważ nie stosów zostanie wykonane.  
  
 Te klasy są deklarowane jako `internal` (`Friend`, w języku Visual Basic) i Zadeklaruj Konstruktor prywatny, aby uniemożliwić tworzenia nowych wystąpień. Metody w tych klas powinny być `static` i `internal` (`Shared` i `Friend` w języku Visual Basic).  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Napraw naruszenie tej reguły, należy przenieść do odpowiedniego metodę **NativeMethods** klasy. W przypadku większości aplikacji przenoszenie P/Invoke do nową klasę o nazwie **NativeMethods** jest wystarczająca.  
  
 Jednak jeśli tworzysz biblioteki do użycia w innych aplikacjach, należy rozważyć dwie klasy, które są nazywane definiowanie **SafeNativeMethods** i **UnsafeNativeMethods**. Te klasy przypominać **NativeMethods** klasy; jednak są oznaczone za pomocą specjalnych atrybut o nazwie **SuppressUnmanagedCodeSecurityAttribute**. Po zastosowaniu tego atrybutu środowisko uruchomieniowe nie przeprowadza przeszukiwania pełnego stosu, aby upewnić się, że wszystkie obiekty wywołujące **UnmanagedCode** uprawnienia. Środowisko uruchomieniowe zwykle sprawdza, czy to uprawnienie podczas uruchamiania. Ponieważ nie jest wykonywane sprawdzanie, może znacznie ulepszyć wydajność w przypadku wywołania tych metod niezarządzane, umożliwia również kod, który ma ograniczone uprawnienia do wywołania tych metod.  
  
 Jednak należy użyć tego atrybutu bardzo ostrożnie. Jeśli wdrażana jest niepoprawnie może mieć wpływ na zabezpieczenia...  
  
 Aby uzyskać informacje dotyczące implementacji metody, zobacz **NativeMethods** przykład **SafeNativeMethods** przykład i **UnsafeNativeMethods** przykład.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje metody, która narusza tę regułę. Aby rozwiązać naruszenie, **RemoveDirectory** P/Invoke powinny zostać przeniesione do odpowiedniej klasy, który jest przeznaczony do przechowywania tylko P/Invoke.  
  
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]  
  
## <a name="nativemethods-example"></a>Przykład NativeMethods  
  
### <a name="description"></a>Opis  
 Ponieważ **NativeMethods** klasy nie powinien być oznaczony za pomocą **SuppressUnmanagedCodeSecurityAttribute**, P/Invoke, które są umieszczane w nim będzie wymagać **UnmanagedCode** uprawnienie. Ponieważ większość aplikacji Uruchom z komputera lokalnego i uruchom wraz z pełnym zaufaniem, to zwykle nie jest problem. Jednak jeśli tworzysz bibliotek wielokrotnego użytku, należy rozważyć definiowanie **SafeNativeMethods** lub **UnsafeNativeMethods** klasy.  
  
 W poniższym przykładzie przedstawiono **Interaction.Beep** metodę, która opakowuje **MessageBeep** funkcji user32.dll. **MessageBeep** P/Invoke jest umieszczany **NativeMethods** klasy.  
  
### <a name="code"></a>Kod  
 [!code-csharp[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]  
  
## <a name="safenativemethods-example"></a>Przykład SafeNativeMethods  
  
### <a name="description"></a>Opis  
 Metody P/Invoke, który można bezpiecznie widoczne dla wszystkich aplikacji i które nie mają żadnych efektów ubocznych należy umieścić w klasie o nazwie **SafeNativeMethods**. Nie masz uprawnień żądanie i nie trzeba zwrócić uwagę znacznie, do której zostaną wywołane.  
  
 W poniższym przykładzie przedstawiono **Environment.TickCount** właściwość, która opakowuje **GetTickCount** funkcji kernel32.dll.  
  
### <a name="code"></a>Kod  
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]  
  
## <a name="unsafenativemethods-example"></a>Przykład UnsafeNativeMethods  
  
### <a name="description"></a>Opis  
 Metody P/Invoke, którego nie można bezpiecznie wywołać i które może wywołać efekty uboczne, które należy umieścić w klasie o nazwie **UnsafeNativeMethods**. Te metody powinny być ściśle sprawdzane, aby upewnić się, że ich nie są widoczne dla użytkownika przypadkowo. Reguła [CA2118: przegląd wykorzystania SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) może to ułatwić. Można również metody powinien mieć uprawnienia innym, jest wymagany, a nie **UnmanagedCode** po ich używają.  
  
 W poniższym przykładzie przedstawiono **Cursor.Hide** metodę, która opakowuje **wartość** funkcji user32.dll.  
  
### <a name="code"></a>Kod  
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Ostrzeżenia projektu](../code-quality/design-warnings.md)