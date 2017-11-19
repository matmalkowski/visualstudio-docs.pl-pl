---
title: "Uzupełnianie za pośrednictwem usługi języka starszych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c694295c3456accc8d2c1cd3b0a1ec20f59343c3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Uzupełnianie składni w starsza wersja usługi języka
Uzupełnianie to proces, za pomocą którego usługa języka umożliwia użytkownikom Zakończ słowem kluczowym języka lub element, który zostały uruchomione, wpisując w edytorze core. W tym temacie omówiono sposób działania uzupełnianie i jak ją wdrożyć w usłudze języka.  
  
 Usługi w starszej wersji języka są zaimplementowane jako część pakiet VSPackage, ale jest nowsza sposób implementowania funkcji usługi języka Aby korzystać z rozszerzeń MEF. Aby dowiedzieć się więcej na temat nowych sposób implementowania uzupełniania instrukcji, zobacz [wskazówki: wyświetlanie uzupełniania](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
>  Zaleca się zacząć Edytor nowy interfejs API tak szybko, jak to możliwe. Spowoduje to poprawić wydajność usługi języka i pozwala korzystać z nowych funkcji edytora.  
  
## <a name="implementing-statement-completion"></a>Implementowanie uzupełniania  
 W edytorze core uzupełniania aktywuje specjalne interfejsu użytkownika, który interaktywnie pomoże Ci łatwo i szybko pisania kodu. Uzupełnianie pomaga wyświetlając odpowiednie obiekty lub klasy, gdy są potrzebne, możesz uniknięcia trzeba pamiętać określonych elementów lub do wyszukania w temacie pomocy odwołania.  
  
 Aby zaimplementować uzupełniania instrukcji, język musi mieć wyzwalacz uzupełniania instrukcji, można przeanalizować. Na przykład [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] użyto operatora kropkę (.), gdy [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] używa strzałka (->) — operator. Usługa języka można użyć więcej niż jeden wyzwalacz zainicjować uzupełniania instrukcji. Te wyzwalacze są zaprogramowane w taki sposób, w filtrze polecenia.  
  
## <a name="command-filters-and-triggers"></a>Polecenie filtrów i wyzwalaczy  
 Polecenie Filtry przechwycić wystąpień wyzwalacza lub wyzwalaczy. Aby dodać filtr polecenia do widoku, zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu i dołącz je do widoku, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody. Można użyć tego samego filtru polecenia (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) za wszystkie aspekty usługi języka, takie jak uzupełnianie, znaczniki błędów i porady — metoda. Aby uzyskać więcej informacji, zobacz [przechwytywaniu polecenia usługi języka starszych](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 Po wprowadzeniu wyzwalacza w edytorze — w szczególności bufor tekstowy — wywołuje usługi języka <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metody. Powoduje to edytor można wyświetlić interfejsu użytkownika, dzięki czemu użytkownik może wybrać spośród kandydatów uzupełniania instrukcji. Ta metoda wymaga wykonania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> i <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> flagi jako parametry. W polu listy przewijania zostanie wyświetlona lista elementów ukończenia. Jako użytkownik będzie nadal występował, wpisując, zaznaczenie w polu listy jest aktualizowany w celu odzwierciedlenia wpisany najlepiej pasuje do najnowszych znaków. Edytor core implementuje interfejs użytkownika dla uzupełniania instrukcji, ale usługa języka musi implementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfejsu do określania zestawu elementów ukończenia candidate dla instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przechwytywaniu polecenia usługi języka starsza wersja](../../extensibility/internals/intercepting-legacy-language-service-commands.md)