---
title: Zapewnianie automatyzacji dla kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f9dbb7a8ddad39f01f5b29443168eebe12a2da8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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
 [Omówienie modelu automatyzacji](../../extensibility/internals/automation-model-overview.md)