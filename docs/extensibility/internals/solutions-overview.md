---
title: "Omówienie rozwiązań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 539ceb45cce6c317ed3723c5006e6d2a77029335
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="solutions-overview"></a>Omówienie rozwiązania
Rozwiązanie to grupa składająca się z jednego lub więcej projektów, które współpracują ze sobą, aby utworzyć aplikację. Projekt i stan informacje dotyczące rozwiązania są przechowywane w dwóch plikach inne rozwiązanie. Plik rozwiązania (sln) jest tekstowy umieszczony pod kontrolą kodu źródłowego i udostępniana między użytkownikami i. Plik rozwiązania użytkownika opcji (.suo) jest plikiem binarnym. W związku z tym plik .suo — nie można umieścić pod kontrolą kodu źródłowego i zawiera informacje specyficzne dla użytkownika.  
  
 Wszelkie pakiet VSPackage może zapisywać do dowolnego typu pliku rozwiązania. Z powodu charakter pliki istnieją dwa różne interfejsy zaimplementowana do zapisu do nich. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> Interfejsu zapisuje informacje tekstowe plik .sln i <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfejsu zapisuje plik .suo strumienie binarne.  
  
> [!NOTE]
>  Projekt nie ma jawnie zapisać wpisu dla siebie w pliku rozwiązania; Środowisko obsługi, który dla projektu. W związku z tym chyba że chcesz dodać dodatkową zawartość specjalnie do pliku rozwiązania, nie trzeba zarejestrować VSPackage w ten sposób.  
  
 Każdy pakiet VSPackage Obsługa rozwiązania trwałości używa trzech interfejsów <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfejsu, który jest implementowany przez środowisko i wywoływana przez pakiet VSPackage, i `IVsPersistSolutionProps` i `IVsPersistSolutionOpts`, są wdrożone zarówno przez pakiet VSPackage. `IVsPersistSolutionOpts` Interfejs tylko musi zostać wdrożone, jeśli ma on zostać zapisany plik .suo przez pakiet VSPackage prywatne informacje.  
  
 Po otwarciu rozwiązania odbywa się następujący proces.  
  
1.  Środowisko odczytuje rozwiązania.  
  
2.  Jeśli znajdzie środowiska `CLSID`, ładuje odpowiedni pakiet VSPackage.  
  
3.  Jeśli pakiet VSPackage zostanie załadowany, wywołania środowiska `QueryInterface` dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interfejsu, interfejsu, który wymaga pakiet VSPackage.  
  
    1.  Podczas odczytu z pliku SLN, środowisko wywołuje `QueryInterface` dla `IVsPersistSolutionProps`.  
  
    2.  Podczas odczytu z pliku .suo, środowisko wywołuje `QueryInterface` dla `IVsPersistSolutionOpts`.  
  
 Informacje szczegółowe dotyczące korzystania z tych plików można znaleźć w [rozwiązania (. Plik sln)](../../extensibility/internals/solution-dot-sln-file.md) i [opcji użytkownika rozwiązania (. Pliku suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
>  Jeśli chcesz utworzyć nową konfigurację rozwiązania składające się z dwóch projektów konfiguracje, z wyłączeniem innej z kompilacji, należy użyć interfejsu użytkownika strony właściwości lub automatyzacji. Nie można zmienić ich właściwości i konfiguracje Menedżera kompilacji rozwiązania bezpośrednio, ale można manipulować Menedżera kompilacji rozwiązania przy użyciu `SolutionBuild` klasy z DTE w modelu automatyzacji. Aby uzyskać więcej informacji na temat konfigurowania rozwiązania, zobacz [konfiguracji rozwiązania](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>