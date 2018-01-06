---
title: "Obsługa narzędzia do przeglądania Symbol | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 78a4e910dbd2c6063f4bdf7b0dff3f27f79b218e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="supporting-symbol-browsing-tools"></a>Obsługa narzędzia do przeglądania Symbol
**Przeglądarka obiektów**, **widoku klasy**, **przeglądarce wywołań** i **wyniki Znajdź Symbol** narzędzia zapewniają symbol Przeglądanie możliwości programu Visual Studio. Te narzędzia wyświetlanie widoków hierarchiczne drzewo symboli i prezentują jedynie relacje między symbolami w drzewie. Symbole może reprezentować przestrzeni nazw, obiektów, klas, elementy członkowskie klasy i inne elementy języka zawarte w różnych składników. Następujące składniki projektów programu Visual Studio, zewnętrznych [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] składniki i biblioteki typów (.tlb). Aby uzyskać więcej informacji, zobacz [wyświetlanie struktury kodu](../../ide/viewing-the-structure-of-code.md).  
  
## <a name="symbol-browsing-libraries"></a>Przeglądanie symbol bibliotek  
 Jako implementujący języka można rozszerzyć możliwości przeglądania symbol Visual Studio, tworząc bibliotek, śledzić symbole w składniki, które stanowią listę symboli do Menedżera obiektów Visual Studio za pomocą zestawu interfejsów. Biblioteki jest opisane przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> interfejsu. Menedżera obiektów Visual Studio odpowiada na żądania dla nowych danych z narzędzia przeglądanie symbol uzyskując dane z biblioteki i organizowanie go. Następnie wypełnia lub aktualizacji narzędzi z żądanych danych. Aby uzyskać odwołania do Menedżera obiektów Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, przekazać <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> identyfikator usługi `GetService` — metoda.  
  
 Każdej biblioteki należy zarejestrować się w Menedżerze obiektów Visual Studio gromadzi informacje o wszystkich bibliotek. Aby zarejestrować bibliotekę, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metody. W zależności od tego, które narzędzie inicjuje żądanie Menedżer obiektów Visual Studio znajdzie odpowiednią bibliotekę i wysyła żądanie danych. Dane przesyłane między bibliotekami i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Menedżera obiektów na listach symboli opisanego przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfejsu.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Menedżera obiektów jest odpowiedzialny za okresowego odświeżania przeglądanie symbol narzędzia do uwzględnienia najnowszych danych zawartych w bibliotekach.  
  
 Na poniższym diagramie podano przykładowe kluczowych elementów procesu wymiany żądań/danych między biblioteką a Menedżera obiektów Visual Studio. Interfejsy na diagramie są częścią aplikacji kodu zarządzanego.  
  
 ![Przepływ danych między biblioteką a Menedżera obiektów](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Zapewnienie list symboli do Menedżera obiektów Visual Studio, najpierw należy zarejestrować bibliotekę z Menedżera obiektów Visual Studio przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metody. Po zarejestrowaniu biblioteki menedżera obiektów Visual Studio żądań niektórych informacji na temat możliwości biblioteki. Na przykład żądania flagi biblioteki i obsługiwane kategorie wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> metody. W pewnym momencie po jednym z narzędzi żąda danych z tej biblioteki menedżera obiektów żąda najwyższego poziomu lista symboli przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> metody. W odpowiedzi, biblioteki wytwarza lista symboli i udostępnia go do Menedżera obiektów Visual Studio za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfejsu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Obiektu manager Określa, ile elementów znajdują się na liście, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> metody. Wszystkie następujące żądania odnoszą się do danego elementu na liście i podaj numer indeksu w każdym żądaniu. Menedżer obiektów Visual Studio będzie kontynuowana, zbierać informacje dotyczące typu, dostępności i inne właściwości elementu przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> metody.  
  
 Określa nazwę elementu wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> — metoda i żąda informacji ikona przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> metody. Ikona jest wyświetlana na lewo od nazwy elementu i przedstawia typu elementu, dostępności i inne właściwości.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Obiekt Menedżera wywołań <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> metodę, aby ustalić, czy element danej listy można rozwijać i zawiera elementy podrzędne. Jeśli interfejsu użytkownika wysyła żądanie do rozszerzenia elementu, Menedżera obiektów żądania podrzędnego lista symboli przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> metody. Proces jest kontynuowany różnych części drzewa tworzone na żądanie.  
  
> [!NOTE]
>  Aby zaimplementować dostawcę symbol kodu natywnego, użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> interfejsów.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: rejestrowanie biblioteki z Menedżera obiektów](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Porady: udostępnianie list symboli udostępniane przez bibliotekę do Menedżera obiektów](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [Instrukcje: identyfikowanie symboli w bibliotece](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)