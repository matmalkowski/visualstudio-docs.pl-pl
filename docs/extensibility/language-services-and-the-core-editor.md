---
title: Usługi językowe i Edytor Core | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cd9e0cdbcb10ac670ac1a0947fb9a43c16c7fccf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138483"
---
# <a name="language-services-and-the-core-editor"></a>Usługi językowe i Edytor Core
Edytory w programie Visual Studio są często powiązane z usługi języka. Między innymi usługi języka zapewnia kolorowanie składni, uzupełniania IntelliSense i formatowania tekstu.  
  
## <a name="core-editors-and-document-data-objects"></a>Edytory podstawowe i obiekty danych dokumentu  
 Po otwarciu edytora core, nie należy tworzyć dane dokumentu i obiekty widoku dokumentu. IDE tworzy i kontroluje te dwa obiekty i wprowadzając odpowiednie wywołania w edytorze wdrożenie fabryki można uzyskać dojścia do nich.  
  
 Aby uzyskać więcej informacji, zobacz [określania edytor, którego otwiera plik w projekcie](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Usługi językowe i Edytor Core  
 Implementacja usługi języka, można kontrolować sposób wyświetlania danych w widoku dokumentu. Usługa języka zawiera informacje i zachowanie, które są specyficzne dla danego języka, takich jak Visual C++. Podczas tworzenia buforu tekstu i określić rozszerzenie nazwy pliku dla dokumentów, które otwierasz, buforu tekstowego określa skojarzony z tym rozszerzeniem nazwy pliku z klucza rejestru, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors usługi języka \\\Extensions {YourLanguageService GUID}. Standardowy pakiet VSPackage ładowania procedury następnie ładuje VSPackage i jest tworzone wystąpienie usługi języka.  
  
 Na poniższej ilustracji przedstawiono usługi podstawowy język.  
  
 ![Grafika przedstawiająca usługi Model języka](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Obiekty usługi Core edytora i język  
  
 Obiekt danych dokumentu edytora core jest nazywana buforu tekstu i jest reprezentowany przez <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu. Obiekt widoku dokumentu nosi nazwę widoku tekstu i jest reprezentowany przez <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> obiektu. Te dwa obiekty współdziałają ze sobą za pośrednictwem usługi języka aby zapewnić spójny obraz edytora core. Informacje z buforu tekstu i wyświetla widok tekstu w oknie dokumentu o nazwie okna kodu. Kod okno dokumentu jest zarządzana przez Menedżera okien kodu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Udostępnia kontekst usługi języka przy użyciu interfejsu API starsza wersja](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [IntelliSense Hosting](../extensibility/intellisense-hosting.md)   
 [Języki zawarte](../extensibility/contained-languages.md)   
 [Tworzenie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)