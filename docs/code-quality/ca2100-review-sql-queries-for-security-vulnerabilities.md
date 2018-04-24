---
title: 'CA2100: Należy przejrzeć zapytania SQL w poszukiwaniu luk w zabezpieczeniach'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 888e80174f34b82c25bc98b8745ae8608322c70c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: Należy przejrzeć zapytania SQL w poszukiwaniu luk w zabezpieczeniach
|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Ustawia metodę <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> właściwości przy użyciu ciąg, który składa się z argumentem ciągu do metody.

## <a name="rule-description"></a>Opis reguły
 Zasada ta zakłada, że argument ciągu zawiera dane wejściowe użytkownika. Ciąg polecenia SQL zbudowany z danych wejściowych użytkownika jest narażony na ataki przez wstrzyknięcie kodu SQL. W celu iniekcji kodu SQL złośliwy użytkownik udostępnia wprowadzania zmieniającą projektu zapytania w celu uszkodzić lub uzyskania nieautoryzowanego dostępu do bazy danych. Typowe techniki to m.in. iniekcji pojedynczy cudzysłów lub apostrof, który jest ogranicznik literału ciągu SQL; dwa łączniki, które oznacza, że komentarz SQL; i średnika, co oznacza, że postępuje nowe polecenie. Jeśli dane wejściowe użytkownika musi być częścią zapytania, użyj jednej z następujących wymienione w kolejności skuteczności, aby zmniejszyć ryzyko ataków.

-   Użyj procedury składowanej.

-   Użyj ciągu sparametryzowanego polecenia.

-   Sprawdzanie poprawności danych wejściowych użytkownika dla typu i zawartości, przed utworzeniem ciąg polecenia.

 Następujące [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] typy implementować <xref:System.Data.IDbCommand.CommandText%2A> właściwość lub ustaw właściwość przy użyciu argument ciągu konstruktorów.

-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> I <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> I <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> I <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> I <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

 Zwróć uwagę, że stosowania metody ToString typu jawnie lub niejawnie naruszenia tej reguły do utworzenia ciągu zapytania. Poniżej przedstawiono przykład.

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 Reguła jest naruszone, ponieważ złośliwy użytkownik może zastąpić metodę ToString().

 Reguła jest również naruszone niejawnie stosowania ToString.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać naruszenie tej reguły, użyj zapytania parametrycznego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli tekst polecenia nie zawiera żadnych danych wejściowych użytkownika.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono metodę, `UnsafeQuery`, który narusza regułę, a także metodę `SaferQuery`, odpowiadającej reguły za pomocą ciągu sparametryzowanego polecenia.

 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]

## <a name="see-also"></a>Zobacz też
 [Przegląd zabezpieczeń](/dotnet/framework/data/adonet/security-overview)