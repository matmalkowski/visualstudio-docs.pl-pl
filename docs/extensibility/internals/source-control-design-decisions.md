---
title: "Decyzje dotyczące projektu w kontroli źródła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 320a8013177d44491470f8f55c8ee3e1fb19501c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-design-decisions"></a>Decyzje dotyczące projektu kontroli źródła
Podczas implementowania kontroli źródła należy rozważyć następujące decyzje dotyczące projektu dla projektów.  
  
## <a name="will-information-be-shared-or-private"></a>Informacje będą udostępnione lub prywatnej?  
 Najważniejsze decyzji projektowej, które można wprowadzić jest jakie informacje są zabezpieczać i co to jest prywatna. Na przykład lista plików dla projektu jest udostępniony, ale w ramach tej listy plików w przypadku niektórych użytkowników może być powoduje, że pliki prywatne. Ustawienia kompilatora są udostępniane, ale projekt rozruchu jest zazwyczaj prywatnych. Ustawienia są wyłącznie udostępnionego, udostępnionych za pomocą zastąpienia lub całkowicie prywatnej. Zgodnie z projektem, prywatne elementy, takie jak rozwiązania użytkownika opcje plików (.suo) nie są sprawdzane w [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]. Należy przechowywać poufnych informacji w plikach prywatnych, takich jak plik .suo lub prywatnej określonego pliku, na przykład można utworzyć,. plik csproj.user Visual C# lub. plik vbproj.user dla języka Visual Basic.  
  
 Ta decyzja nie udostępnia i będzie możliwe na podstawie elementu —.  
  
## <a name="will-the-project-include-special-files"></a>Projekt będzie zawierać specjalne pliki?  
 Innej decyzji projektowych ważne jest, czy struktury projektu używa plików specjalnych. Specjalne pliki są ukryte pliki, które opierają się pliki, które są widoczne w Eksploratorze rozwiązań i zaewidencjonowania i wyewidencjonowania okien dialogowych. Jeśli używasz specjalne pliki, zgodna z tymi wytycznymi:  
  
1.  Nie należy kojarzyć specjalne pliki z węzła głównego projektu — to znaczy w projekcie samym pliku. Plik projektu musi być pojedynczym pliku.  
  
2.  Gdy specjalne pliki są dodane, usunięte lub zmieniono jego nazwę w projekcie odpowiednich <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> zdarzenia musi być wywoływane z ustawioną flagą wskazującą są specjalne pliki. Te zdarzenia są wywoływane przez środowisko w odpowiedzi na wywołanie odpowiedni projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> metody.  
  
3.  Gdy wywołuje projekcie lub edytor <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> dla pliku, specjalne pliki skojarzone z tym plikiem nie zostały automatycznie wyewidencjonowane. Przekaż specjalne pliki w wraz z pliku nadrzędnym. Środowisko wykryje relacji między wszystkie pliki, które są przekazywane w i odpowiednio Ukryj specjalne pliki w Interfejsie użytkownika wyewidencjonowywania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Obsługa kontroli źródła](../../extensibility/internals/supporting-source-control.md)