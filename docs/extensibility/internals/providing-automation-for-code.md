---
title: Zapewnianie automatyzacji dla kodu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aa1c2fa5d0da738057e59cdac007c499a834bc0a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="providing-automation-for-code"></a>Zapewnianie automatyzacji dla kodu
Tworzenie modelu automatyzacji dla kodu nie jest wymagane. Zestaw SDK środowiska nie przewiduje próbkę w ten sposób. Szczegółowe informacje na temat modele kodu, zobacz <xref:EnvDTE.CodeModel> obiektu.  
  
 Aby wdrożyć model kodu, musi implementować żadnych interfejsów, które są określane przez strukturę danych wewnętrznych. Obiekt musi pochodzić z `IDispatch` klasy.  
  
 Obiekty, które można rozszerzyć <xref:EnvDTE.CodeModel> i <xref:EnvDTE.FileCodeModel>, są dostępne z <xref:EnvDTE.Project> obiektu i wyglądać następująco:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Można wybrać do zaimplementowania tylko `CodeModel` lub `FileCodeModel` interfejsu w obiekcie zwróconych z Twojej `Project` i <xref:EnvDTE.ProjectItem> obiektów. Można korzystać z funkcji w tym interfejsie, który jest odpowiedni dla systemu projektu.  
  
 Jeśli chcesz dodać funkcje, takie jak metody lub właściwości, które nie są dostępne ze standardu `CodeModel` i `FileCodeModel` interfejsów, utworzyć własny interfejs, który dziedziczy standardowego. Pamiętaj dokumentu z systemu projektu, aby wiedzieli, że użytkownicy końcowi poszukaj go. Zwraca standardowy interfejs, ale użytkownik może wywołać `QueryInterface` metody lub Rzutowanie do interfejsu Jeżeli wiadomo istnieje.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd modelu automatyzacji](../../extensibility/internals/automation-model-overview.md)