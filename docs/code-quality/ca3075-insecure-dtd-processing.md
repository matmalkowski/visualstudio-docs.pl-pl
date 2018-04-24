---
title: 'CA3075: Przetwarzanie DTD niezabezpieczonych'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b288ba61a4e5ee1d8df60d9ac4c250f2ec7081d2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075: Przetwarzanie DTD niezabezpieczonych
|||
|-|-|
|TypeName|InsecureDTDProcessing|
|CheckId|CA3075|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Jeśli używasz niezabezpieczonych <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> wystąpień lub odwołanie do zewnętrznej jednostki źródeł, analizator akceptuje niezaufanych argument wejściowy i argument wyjawiać poufnych informacji do osoby atakujące.

## <a name="rule-description"></a>Opis reguły
 A *definicji typu dokumentu (DTD)* jest jeden z dwóch sposobów analizatora składni XML można określić ważności dokumentu, zgodnie z definicją w [sieci World Wide Web konsorcjum W3C XML Extensible Markup Language () 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Ta reguła ma właściwości i gdzie niezaufanych danych jest akceptowany w celu ostrzegania o deweloperów o możliwości wystąpienia [ujawnienie informacji](/dotnet/framework/wcf/feature-details/information-disclosure) zagrożenia, które mogą prowadzić do [przeprowadzenie ataku typu "odmowa usługi" (DoS)](/dotnet/framework/wcf/feature-details/denial-of-service) ataków. Ta zasada wyzwala, gdy:

-   Włączono DtdProcessing <xref:System.Xml.XmlReader> wystąpienia, która rozpoznaje zewnętrznej jednostki XML przy użyciu <xref:System.Xml.XmlUrlResolver>.

-   <xref:System.Xml.XmlNode.InnerXml%2A> Ustawiono właściwość w pliku XML.

-   <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> Właściwość jest ustawiona do analizy.

-   Niezaufane danych wejściowych jest przetwarzana z użyciem <xref:System.Xml.XmlResolver> zamiast <xref:System.Xml.XmlSecureResolver> .

-   Element XmlReader.<xref:System.Xml.XmlReader.Create%2A> Metoda jest wywoływana z niezabezpieczonych <xref:System.Xml.XmlReaderSettings> wystąpienia lub nie wcale.

-   <xref:System.Xml.XmlReader> tworzona jest niebezpieczne domyślne ustawienia lub wartości.

 W każdym z tych przypadków, wynikiem jest taki sam: zawartość z albo udziałami plików w systemie lub w sieci z komputera przetwarzania pliku XML mają być widoczne dla osoby atakującej, może być następnie użyta jako wektor DoS.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

-   CATCH i przetwórz wszystkie wyjątki klasy XmlTextReader właściwie, aby uniknąć ścieżki ujawnienie informacji.

-   Użyj <xref:System.Xml.XmlSecureResolver> ograniczyć zasoby, które mogą uzyskiwać dostęp do klasy XmlTextReader.

-   Nie zezwalaj na <xref:System.Xml.XmlReader> otworzyć dowolnych zasobów zewnętrznych, ustawiając <xref:System.Xml.XmlResolver> właściwości **null**.

-   Upewnij się, że <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A> właściwość <xref:System.Data.DataViewManager> przypisano z zaufanego źródła.

 .NET 3.5 lub starszy

-   Wyłącz DTD przetwarzania czy mamy do czynienia ze źródeł niezaufanych przez ustawienie <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> właściwości **true** .

-   Klasy XmlTextReader ma żądanie dziedziczenia pełnego zaufania.

 .NET 4 i nowsze

-   Unikaj włączania DtdProcessing, jeśli jest zajmujących źródeł niezaufanych, ustawiając <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A?displayProperty=nameWithType> właściwości **Zabroń** lub **Ignoruj**.

-   Upewnij się, że we wszystkich przypadkach InnerXml metoda Load() korzysta z wystąpienia elementu XmlReader.

> [!NOTE]
>  Ta zasada może raportować fałszywych alarmów na niektórych wystąpień prawidłową XmlSecureResolver. Pracujemy nad rozwiązywania tego problemu przez środek 2016.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli nie masz pewności, czy dane wejściowe jest znany jako z zaufanego źródła, nie Pomijaj reguły z to ostrzeżenie.

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

### <a name="violation"></a>Naruszenie

```csharp
using System.IO;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlSchema schema = XmlSchema.Read(tr, null); // warn
            return schema;
        }
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System.IO;
using System.Xml;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlTextReader reader = new XmlTextReader(tr) { DtdProcessing = DtdProcessing.Prohibit };
            XmlSchema schema = XmlSchema.Read(reader , null);
            return schema;
        }
    }
}
```

### <a name="violation"></a>Naruszenie

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings();
        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);  // warn
        }
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings()
        {
            DtdProcessing = DtdProcessing.Prohibit
        };

        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);
        }
    }
}
```

### <a name="violations"></a>Naruszenia

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseSetInnerXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument() { XmlResolver = null };
            doc.InnerXml = xml; // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseLoadXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument(){ XmlResolver = null };
            doc.LoadXml(xml); // warn
        }
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System.Xml;

public static void TestMethod(string xml)
{
    XmlDocument doc = new XmlDocument() { XmlResolver = null };
    System.IO.StringReader sreader = new System.IO.StringReader(xml);
    XmlTextReader reader = new XmlTextReader(sreader) { DtdProcessing = DtdProcessing.Prohibit };
    doc.Load(reader);
}
```

### <a name="violation"></a>Naruszenie

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            serializer.Deserialize(stream); // warn
        }
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            XmlTextReader reader = new XmlTextReader(stream) { DtdProcessing = DtdProcessing.Prohibit } ;
            serializer.Deserialize(reader );
        }
    }
}
```

### <a name="violation"></a>Naruszenie

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XPathDocument doc = new XPathDocument(path); // warn
        }
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XmlTextReader reader = new XmlTextReader(path) { DtdProcessing = DtdProcessing.Prohibit };
            XPathDocument doc = new XPathDocument(reader);
        }
    }
}
```

### <a name="violation"></a>Naruszenie

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = new XmlUrlResolver() };
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = null }; // or set to a XmlSecureResolver instance
    }
}
```

### <a name="violations"></a>Naruszenia

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Parse };
            XmlReader reader = XmlReader.Create(path, settings); // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod()
        {
            var reader = XmlTextReader.Create(""doc.xml""); //warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            try {
                XmlTextReader reader = new XmlTextReader(path); // warn
            }
            catch { throw ; }
            finally {}
        }
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Prohibit };
            XmlReader reader = XmlReader.Create(path, settings);
        }
    }
}
```