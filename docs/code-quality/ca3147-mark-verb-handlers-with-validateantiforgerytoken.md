---
title: 'CA3147: Oznacz zlecenie obsługi za pomocą ValidateAntiForgeryToken'
ms.date: 08/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 4b4369cfd310be9322d17b8bdbfe79880f2aa579
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40009050"
---
# <a name="ca3147-mark-verb-handlers-with-validateantiforgerytoken"></a>CA3147: Oznacz zlecenie obsługi za pomocą ValidateAntiForgeryToken

|||
|-|-|
|TypeName|MarkVerbHandlersWithValidateAntiForgeryToken|
|CheckId|CA3147|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Metody akcji kontrolera ASP.NET MVC nie jest oznaczona za pomocą <xref:Microsoft.AspNetCore.Mvc.ValidateAntiForgeryTokenAttribute?displayProperty=fullName>, lub atrybutu określenie zlecenie HTTP, takich jak <xref:Microsoft.AspNetCore.Mvc.HttpGetAttribute?displayProperty=fullName> lub <xref:Microsoft.AspNetCore.Mvc.AcceptVerbsAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły

Podczas projektowania kontroler składnika ASP.NET MVC, należy zachować ostrożność, fałszerstwo żądania międzywitrynowego ataków. Ataku polegającego na fałszerstwo żądania międzywitrynowego można wysyłać złośliwymi żądaniami z uwierzytelnionego użytkownika do kontrolera ASP.NET MVC. Aby uzyskać więcej informacji, zobacz [zapobieganie XSRF/CSRF w ASP.NET MVC i web pages](/aspnet/mvc/overview/security/xsrfcsrf-prevention-in-aspnet-mvc-and-web-pages).

Ta reguła sprawdza kontrolera ASP.NET MVC metod akcji albo:

- Masz <xref:Microsoft.AspNetCore.Mvc.ValidateAntiForgeryTokenAttribute> i określić dozwolonych poleceń HTTP, nie wliczając HTTP GET.

- Określ HTTP GET, jako dozwolone zlecenie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Dla akcji kontrolera ASP.NET MVC obsługuje żądania HTTP GET, które nie mają potencjalnie szkodliwe efekty uboczne, Dodaj <xref:Microsoft.AspNetCore.Mvc.HttpGetAttribute> do metody.

   W przypadku platformy ASP.NET MVC akcji kontrolera, który obsługuje HTTP GET żądania i ma potencjalnie szkodliwe efekty uboczne, takie jak modyfikowanie danych poufnych aplikacji jest narażony na fałszerstwo żądania międzywitrynowego ataków.  Należy ponownie zaprojektować aplikację tak, aby tylko żądania HTTP POST, PUT i DELETE wykonywać operacje poufnych.

- Dla akcji kontrolera ASP.NET MVC, które obsługują żądania HTTP POST, PUT lub DELETE żądań, Dodaj <xref:Microsoft.AspNetCore.Mvc.ValidateAntiForgeryTokenAttribute> i atrybuty określające dozwolonych poleceń HTTP (<xref:Microsoft.AspNetCore.Mvc.AcceptVerbsAttribute>, <xref:Microsoft.AspNetCore.Mvc.HttpPostAttribute>, <xref:Microsoft.AspNetCore.Mvc.HttpPutAttribute>, lub <xref:Microsoft.AspNetCore.Mvc.HttpDeleteAttribute>). Ponadto należy wywołać <xref:Microsoft.AspNetCore.Mvc.ViewFeatures.HtmlHelper.AntiForgeryToken%2A?displayProperty=nameWithType> z widoku składnika MVC lub strony sieci web Razor. Aby uzyskać przykład, zobacz [badanie metod edycji i widoku edycji](/aspnet/mvc/overview/getting-started/introduction/examining-the-edit-methods-and-edit-view).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest to bezpieczne Pomijaj ostrzeżeń dla tej reguły, jeśli:

- Akcja kontrolera ASP.NET MVC nie ma szkodliwego wpływu po stronie.

- Aplikacja sprawdza poprawność tokenu antiforgery w inny sposób.

## <a name="validateantiforgerytoken-attribute-example"></a>Przykład atrybutu ValidateAntiForgeryToken

### <a name="violation"></a>Naruszenie zasad

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            // You don't want an attacker to specify to who and how much money to transfer.

            return null;
        }
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            return null;
        }
    }
}
```

## <a name="httpget-attribute-example"></a>Przykład atrybutu HttpGet

### <a name="violation"></a>Naruszenie zasad

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult Help(int topicId)
        {
            // This Help method is an example of a read-only operation with no harmful side effects.
            return null;
        }
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpGet]
        public ActionResult Help(int topicId)
        {
            return null;
        }
    }
}
```
