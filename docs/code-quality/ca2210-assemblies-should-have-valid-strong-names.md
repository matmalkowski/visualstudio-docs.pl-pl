---
title: 'CA2210: Zestawy powinny mieć prawidłowe silne nazwy'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b7421cee4e1b561d4efec7b843d12a7dcf5a67a6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Zestawy powinny mieć prawidłowe silne nazwy
|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Zestaw nie jest podpisany przy użyciu silnej nazwy nie można zweryfikować silnej nazwy lub silnej nazwy nie jest prawidłowym bez bieżących ustawień rejestru komputera.

## <a name="rule-description"></a>Opis reguły
 Ta zasada pobiera i weryfikuje silnej nazwy zestawu. Naruszenie wystąpi, jeśli spełnione są następujące:

-   Zestaw nie ma silnej nazwy.

-   Zestaw został zmieniony po podpisywania.

-   Zestaw jest podpisywany z opóźnieniem.

-   Zestaw został podpisany niepoprawnie lub podpisanie nie powiodło się.

-   Zestaw wymaga zmiany ustawień rejestru do przekazania weryfikacji. Na przykład przez narzędzie Strong Name (Sn.exe) została użyta do pominięcia weryfikacji dla zestawu.

 Silna nazwa chroni klientów przed nieświadomym ładowaniem zestawu, który został zmieniony. Zestawy bez silnej nazwy nie powinny być wdrażane poza bardzo ograniczonymi scenariuszami. Jeśli użytkownik udostępnia lub dystrybuuje zestawy, które nie są poprawnie podpisane, zestaw może zostać zmieniony, środowisko uruchomieniowe języka wspólnego może nie załadować zestawu lub użytkownik będzie musiał wyłączyć weryfikację na swoim komputerze. Ma zestawu bez silnej nazwy z następujące wady:

-   Nie można zweryfikować jego źródła.

-   Środowisko uruchomieniowe języka wspólnego nie ostrzegaj użytkowników, jeśli zawartość zestawu została zmieniona.

-   Nie można załadować do pamięci podręcznej GAC.

 Należy pamiętać, że można załadować i przeanalizować zestawem podpisywany z opóźnieniem, należy wyłączyć weryfikację dla zestawu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 **Aby utworzyć plik klucza**

 Użyj jednej z następujących procedur:

-   Użyj narzędzia Assembly Linker (Al.exe) udostępniane przez [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zestawu SDK.

-   Aby uzyskać [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 1.0 lub 1.1, użyj jednej <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> lub <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> atrybutu.

-   Aby uzyskać [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], użyj jednej `/keyfile` lub `/keycontainer` — opcja kompilatora [/KeyFile (Określ klucz lub parę klucz Aby podpisać zestaw)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly) lub  [ /KeyContainer (Określanie kontenera klucza, aby podpisać zestaw)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) w języku C++ — opcja konsolidatora).

 **Aby zarejestrować używanemu zestawowi silną nazwą w programie Visual Studio**

1.  W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], otwórz rozwiązanie.

2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości.**

3.  Kliknij przycisk **podpisywanie** , a następnie wybierz **Podpisz zestaw** pole wyboru.

4.  Z **wybierz plik klucza o silnej nazwie**, wybierz pozycję **nowy**.

     **Tworzenie silnej nazwy klucza** oknie będą wyświetlane.

5.  W **nazwę pliku klucza**, wpisz nazwę klucza silnej nazwy.

6.  Określ, czy do ochrony klucza z hasła, a następnie kliknij przycisk **OK**.

7.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **kompilacji**.

 **Aby zarejestrować używanemu zestawowi silną nazwą poza programem Visual Studio**

-   Użyj narzędzia silnej nazwy (Sn.exe) dostarczonego przez [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zestawu SDK. Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie silnej nazwy)](/dotnet/framework/tools/sn-exe-strong-name-tool).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Tylko pominąć ostrzeżenie od tej reguły, jeśli zestaw jest używany w środowisku, w których wprowadzanie zmian w zawartości nie ma znaczenia.

## <a name="see-also"></a>Zobacz też
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> [Porady: podpisać zestaw o silnej nazwie](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name) [Sn.exe (narzędzie silnych nazw)](/dotnet/framework/tools/sn-exe-strong-name-tool)