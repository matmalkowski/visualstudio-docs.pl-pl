---
title: Uzyskiwanie dostępu do danych w dokumentach na serwerze
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ecfebda02096d1a36a5de84919aad65482a25ec0
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="access-data-in-documents-on-the-server"></a>Uzyskiwanie dostępu do danych w dokumentach na serwerze
  Można programu z danymi w dostosowaniu poziomie dokumentu, bez konieczności używania modelu obiektów programu Microsoft Office Word i Microsoft Office Excel. Oznacza to, że można uzyskać dostępu do danych znajdujących się w dokumencie na serwerze, który nie ma programu Word lub zainstalowany program Excel. Na przykład kodu na serwerze (na przykład w [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] strony) można dostosować dane w dokumencie i wysłać dokument dostosowane do użytkownika końcowego. Gdy użytkownik końcowy otworzy dokumentu, kod powiązania danych w zestawie rozwiązanie wiąże danych dostosowane do dokumentu. Jest to możliwe, ponieważ dane w dokumencie jest oddzielony od interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [buforowane dane w dostosowaniach na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md).  

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

## <a name="cache-data-for-use-on-a-server"></a>Pamięć podręczna danych do użycia na serwerze  
 W pamięci podręcznej obiektu danych w dokumencie, oznacz go z <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybutu w czasie projektowania, lub użyj `StartCaching` metody elementu hosta w czasie wykonywania. Gdy buforowanie obiektu danych w dokumencie [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializuje obiekt do ciągu XML, który jest przechowywany w dokumencie. Obiekty muszą spełniać określone wymagania na kwalifikować się do buforowania. Aby uzyskać więcej informacji, zobacz [dane z pamięci podręcznej](../vsto/caching-data.md).  

 Kod po stronie serwera można manipulować obiektów danych w pamięci podręcznej danych. Formanty powiązane z wystąpień buforowane dane są synchronizowane z interfejsu użytkownika tak, aby zmiany po stronie serwera, które zostały wprowadzone dane wyświetlane automatycznie po otwarciu dokumentu na kliencie.  

## <a name="access-data-in-the-cache"></a>Uzyskiwanie dostępu do danych w pamięci podręcznej  
 Można uzyskać dostępu do danych w pamięci podręcznej z poziomu aplikacji poza biurem, na przykład z aplikacji konsoli, aplikacji formularzy systemu Windows lub strony sieci Web. Aplikacja, która uzyskuje dostęp do pamięci podręcznej danych musi mieć pełne zaufanie; aplikacji sieci Web, który ma częściowej relacji zaufania nie można wstawić, pobrać lub zmień dane są buforowane w dokumencie programu Word.  

 Pamięć podręczna danych jest dostępna za pośrednictwem hierarchii kolekcje są udostępniane przez <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> właściwość <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy:  

-   <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> Zwraca <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>, który zawiera wszystkie buforowane dane w dostosowaniu poziomie dokumentu.  

-   Każdy <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> zawiera jeden lub więcej <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> obiektów. A <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> zawiera wszystkie obiekty danych z pamięci podręcznej, które są zdefiniowane w ramach jednej klasy.  

-   Każdy <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> zawiera jeden lub więcej <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> obiektów. A <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> reprezentuje obiekt pojedynczego dane z pamięci podręcznej.  

 W poniższym przykładzie pokazano, jak uzyskać dostępu do pamięci podręcznej ciągów w `Sheet1` klasy projektu skoroszyt programu Excel. Ten przykład jest częścią większego przykładu udostępnionego dla <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metody.  

 [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
 [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]  

## <a name="modify-data-in-the-cache"></a>Modyfikowanie danych w pamięci podręcznej  
 Aby zmodyfikować obiekt danych z pamięci podręcznej, zazwyczaj należy wykonać następujące czynności:  

1.  Deserializacja reprezentację XML obiektu w pamięci podręcznej do nowego wystąpienia obiektu. Dostęp do pliku XML przy użyciu <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> właściwość <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> reprezentujący obiekt danych z pamięci podręcznej.  

2.  Wprowadź zmiany w tej kopii.  

3.  Serializacji obiektu zmienione do pamięci podręcznej danych przy użyciu jednej z następujących opcji:  

    -   Jeśli chcesz automatycznie serializuj zmiany, użyj <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metody. Ta metoda używa **elementu DiffGram** format serializacji <xref:System.Data.DataSet>, <xref:System.Data.DataTable>i typizowanych obiektów dataset w pamięci podręcznej danych. **Elementu DiffGram** format gwarantuje, że zmiany w pamięci podręcznej danych w dokumencie w trybie offline są prawidłowo wysyłane do serwera.  

    -   Jeśli chcesz wykonać własne serializacji zmiany danych z pamięci podręcznej, można wpisać bezpośrednio do <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> właściwości. Określ **elementu DiffGram** formatowanie, jeśli używasz <xref:System.Data.Common.DataAdapter> do aktualizacji bazy danych ze zmianami wprowadzonymi danymi w <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, lub wpisane zestawu danych. W przeciwnym razie <xref:System.Data.Common.DataAdapter> spowoduje zaktualizowanie bazy danych przez dodanie nowych wierszy zamiast modyfikowania istniejących wierszy.  

### <a name="modify-data-without-deserializing-the-current-value"></a>Modyfikowanie danych bez podczas deserializacji, bieżąca wartość  
 W niektórych przypadkach można zmodyfikować wartości obiektu w pamięci podręcznej bez pierwszy deserializacji, bieżąca wartość. Na przykład można to zrobić w przypadku zmiany wartości obiektu, który ma typ prosty, takiego jak ciąg lub liczba całkowita, lub jeśli są inicjowanie buforowane <xref:System.Data.DataSet> w dokumencie na serwerze. W takich przypadkach można użyć <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metody bez pierwszy deserializacji, bieżąca wartość obiektu w pamięci podręcznej.  

 Poniższy przykład kodu pokazuje, jak zmienić wartości ciąg pamięci podręcznej w `Sheet1` klasy projektu skoroszyt programu Excel. Ten przykład jest częścią większego przykładu udostępnionego dla <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metody.  

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]  

### <a name="modify-null-values-in-the-data-cache"></a>Zmodyfikuj wartości null w pamięci podręcznej danych  
 Pamięć podręczna danych nie przechowuje obiekty, które mają wartość **null** gdy dokumentu jest zapisane i zamknięte. To ograniczenie ma kilka konsekwencje po zmodyfikowaniu danych z pamięci podręcznej:  

-   Jeśli ustawisz dowolnego obiektu w pamięci podręcznej danych z wartością **null**, wszystkie obiekty w pamięci podręcznej danych zostanie automatycznie ustawione na **null** po otwarciu dokumentu i danych pamięci podręcznej zostanie usunięty podczas dokument jest zapisany i zamknięte. Oznacza to, że wszystkie obiekty pamięci podręcznej zostanie usunięty z pamięci podręcznej danych i <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> kolekcja będzie pusta.  

-   W przypadku tworzenia rozwiązania z **null** obiektów w pamięci podręcznej danych i chcesz zainicjować tych obiektów przy użyciu <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy przed dokument jest otwarty po raz pierwszy, należy zapewnić, inicjowanie wszystkich obiektów w pamięci podręcznej danych. Jeśli musisz zainicjować niektórych obiektów, wszystkie obiekty zostanie ustawiona do **null** po otwarciu dokumentu i pamięci podręcznej danych zostanie wyczyszczona po zapisaniu dokumentu i zamknięte.  

## <a name="access-typed-datasets-in-the-cache"></a>Dostęp wpisanych zestawów danych w pamięci podręcznej  
 Jeśli chcesz uzyskać dostęp do danych typizowanego zestaw danych, zarówno z rozwiązania do pakietu Office i aplikacji poza biurem, takich jak aplikacji formularzy systemu Windows lub [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] projektu, należy zdefiniować typizowanego obiektu dataset w osobny zestaw, do którego odwołuje się zarówno w projekty. Jeśli dodasz typizowany zestaw danych do każdego projektu za pomocą **konfiguracji źródła danych** kreatora lub **Projektant obiektów Dataset**, .NET Framework w dwa projekty jako różne typy, będą traktować typizowane zbiory danych . Aby uzyskać więcej informacji o tworzeniu typizowane zbiory danych, zobacz [tworzenie i konfigurowanie zestawów danych w programie Visual Studio](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).  

## <a name="see-also"></a>Zobacz także  
 [Uzyskiwanie dostępu do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Buforowane dane w dostosowaniach na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md)  
