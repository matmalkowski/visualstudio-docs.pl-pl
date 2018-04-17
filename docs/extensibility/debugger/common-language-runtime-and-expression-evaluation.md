---
title: Środowisko uruchomieniowe języka wspólnego i Obliczanie wyrażenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 370b7963c71b74674c7d323a5fa1c2650d3f08d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Środowisko uruchomieniowe języka wspólnego i Szacowanie wyrażeń
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Kompilatory, takie jak Visual Basic i C# (Wymowa C sharp), który docelowe środowisko uruchomieniowe języka wspólnego (CLR), należy utworzyć Microsoft pośredniego języka (MSIL), która jest nowsza skompilowanych do natywnego kodu. Środowisko CLR zawiera aparat debugowania (DE), aby debugować kod wynikowy. Jeśli planujesz przeprowadzić integrację zastrzeżonych języka programowania Visual Studio IDE, można skompilować do MSIL i dlatego nie trzeba napisać własne DE. Jednak należy zapisać ewaluatora wyrażeń (EE), który jest w stanie obliczenia wyrażenia w kontekście języka programowania.  
  
## <a name="discussion"></a>Omówienie  
 Wyrażenia języka komputera zazwyczaj są parsowane do produkcji zestaw obiektów danych i operatorów używane do manipulowania nimi. Na przykład wyrażenie "A + B" może być analizowana zastosować operator dodawania (+) do danych obiektów "A" i "B", co prawdopodobnie w innym obiekcie danych. Całkowita zestaw obiektów danych, Operatorzy i ich skojarzenia najczęściej są reprezentowane w programie jako drzewo z operatorów w węzłach drzewa i obiekty danych, w gałęzi. Wyrażenie, które podziale w formie drzewa jest często nazywana przeanalizowany drzewa.  
  
 Po przeanalizowaniu wyrażenia do oceny każdego obiektu danych nosi nazwę dostawcy symbolu (SP). Na przykład "A" zdefiniowano zarówno w więcej niż jedną metodę, a następnie pytanie "Które A?" należy udzielić odpowiedzi, zanim może być ustalona wartość A. Odpowiedź zwrócona przez PS jest podobny do "Trzeci element na piąty ramki stosu" lub "A, który jest 50 bajtów poza początku pamięci statycznej przydzielony do tej metody."  
  
 Oprócz dla sam program, który wygenerował MSIL, kompilatory CLR można utworzyć również bardzo opisowe informacje debugowania, który jest zapisany w pliku bazy danych programu (PDB). Tak długo, jak kompilatora języka zastrzeżonych generuje informacje o debugowaniu w tym samym formacie co kompilatory CLR, mógł zidentyfikować, że języka o nazwie obiektów danych jest SP CLR. Po zidentyfikowaniu obiektu danych o nazwie EE używa obiektu wiążącego skojarzyć (lub powiązać) obiekt danych do obszaru pamięci, która przechowuje wartość tego obiektu. Niemcy można pobrać lub ustawić nową wartość dla obiekt danych.  
  
 Zastrzeżonych kompilatora zapewniają CLR informacji o debugowaniu wywołując `ISymbolWriter` interfejsu (która jest zdefiniowana w programie .NET Framework w przestrzeni nazw `System.Diagnostics.SymbolStore`). Kompilowanie do MSIL i zapisywania informacji debugowania za pomocą tych interfejsów, użyć zastrzeżonych kompilatora CLR DE i dostawcę usługi. Znacznie ułatwia integrowanie właściwy język środowiska IDE programu Visual Studio.  
  
 Gdy CLR DE wywołuje zastrzeżonych EE można obliczyć wyrażenia, DE dostarcza EE z interfejsami SP i obiektu wiążącego. W związku z tym zapisywania oznacza aparat debugowania na podstawie CLR jest konieczne tylko implementować interfejsów ewaluatora wyrażenia odpowiednie; Środowisko CLR odpowiada on za powiązania i symbol obsługi dla Ciebie.  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie Ewaluator wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)