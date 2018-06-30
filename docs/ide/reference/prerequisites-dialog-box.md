---
title: Wstępnie wymagane składniki — Okno dialogowe
ms.date: 06/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1360b63eb1469efe4948f2859e28a567b00ad1a
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117267"
---
# <a name="prerequisites-dialog-box"></a>Wstępnie wymagane składniki — Okno dialogowe

**Wymagania wstępne** okno dialogowe Określa zainstalowane wstępnie wymagane składniki, jak są zainstalowane i które kolejność, są zainstalowane pakiety.

![Okno dialogowe wymagań wstępnych w programie Visual Studio](media/prerequisites-dialog-box.png)

Aby otworzyć okno dialogowe, wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie wybierz **projektu** > **właściwości**. Gdy **projektanta projektu** zostanie wyświetlone, wybierz **publikowania** , a następnie wybierz **wymagania wstępne**. Dla projektów instalacji na **projektu** menu, kliknij przycisk **właściwości**. Gdy **strony właściwości** zostanie wyświetlone okno dialogowe, kliknij przycisk **wymagania wstępne**.

## <a name="uielement-list"></a>Lista elementów interfejsu użytkownika

|Element|Opis|
|-------------|-----------------|
|**Utwórz program instalacyjny, aby zainstalować wstępnie wymagane składniki**|Zawiera składniki wymagane wstępnie programu instalacyjnego (*Setup.exe*), dzięki czemu będzie można zainstalować przed aplikacji, w kolejności zależności. Domyślnie ta opcja jest zaznaczona. Jeśli nie jest zaznaczone, nie *Setup.exe* jest tworzony.|
|**Wybierz wstępnie wymagane składniki do zainstalowania**|Określa, czy należy zainstalować składniki, takie jak bibliotek środowiska uruchomieniowego .NET Framework i C++.<br /><br />Na przykład przez zaznaczenie pola wyboru obok pozycji **programu SQL Server 2012 Express**, możesz określić, że program instalacyjny należy sprawdzić, czy ten składnik jest zainstalowany na komputerze docelowym i zainstalować go, jeśli nie jest.<br /><br />Aby uzyskać szczegółowe informacje dotyczące każdego pakietu wymagań wstępnych, zobacz [informacje o wymaganiach wstępnych](#prerequisites-information).|
|**Pobierz wstępnie wymagane składniki z witryny dostawcy składników**|Określa, że wstępnie wymagane składniki zostanie zainstalowany z witryny sieci Web dostawcy. Jest to opcja domyślna.|
|**Pobierz wstępnie wymagane składniki z tej samej lokalizacji co Moja aplikacja**|Określa, czy wstępnie wymagane składniki zostanie zainstalowany z tej samej lokalizacji co aplikacja. Wszystkie wstępnie wymagane pakiety zostanie skopiowana do lokalizacji publikacji. Aby opcja działała, składniki muszą się znajdować na komputerze deweloperskim.|
|**Pobierz wstępnie wymagane składniki z następującej lokalizacji**|Określa, czy wstępnie wymagane składniki zostanie zainstalowany z lokalizacji, które można wprowadzić. Można użyć **Przeglądaj** przycisk, aby wybrać lokalizację.|

## <a name="prerequisites-information"></a>Informacje o wymaganiach wstępnych

Wymagane składniki, które są widoczne w **wymagania wstępne** okno dialogowe mogą różnić się od tych na poniższej liście. Wstępnie wymagane pakiety wymienione w **wstępnie wymagane składniki — okno dialogowe** są ustawiane automatycznie przy pierwszym otwarciu okna dialogowego. Jeśli użytkownik zmieni platformy docelowej projektu, trzeba wybrać wymagania wstępne ręcznie, aby dopasować nowej platformy docelowej.

|Element|Opis|
|-------------|-----------------|
|**.NET framework 3.5 z dodatkiem SP1**|Ten pakiet instaluje następujące czynności:<br /><br /> -.NET framework w wersji 2.0, 3.0 i 3.5.<br />-Obsługa wszystkich wersji systemu .NET Framework w 32-bitowych (x86) i (x64) 64-bitowych systemach operacyjnych.<br />— Pakiety językowe dla każdej wersji .NET Framework, który ma zainstalowany pakiet.<br />-Dodatki service Pack dla programu .NET Framework 2.0 i 3.0.<br /><br /> .NET framework 3.0 jest dołączony do systemu Windows Vista i .NET Framework 3.5 jest dołączana do programu Visual Studio. .NET framework 3.5 jest wymagana dla wszystkich projektów Visual Basic i C#, które są kompilowane dla 32-bitowych systemów operacyjnych i która platforma docelowa ma wartość **.NET Framework 3.5**, a dla projektów Visual Basic i C# skompilowana dla wersji 64-bitowych systemy operacyjne. (IA64 nie jest obsługiwana.) Należy pamiętać, że projekty Visual Basic i C# są kompilowane dla dowolnej architektury Procesora domyślnie. Aby uzyskać więcej informacji, zobacz [programu Visual Studio omówienie Wielowersyjności](../../ide/visual-studio-multi-targeting-overview.md) i [wdrożyć wymagania wstępne dotyczące aplikacji 64-bitowych](../../deployment/deploying-prerequisites-for-64-bit-applications.md).|
|**Microsoft .NET Framework 4.x**|Ten pakiet instaluje program .NET Framework 4.x x86 i x64 64.|
|**Microsoft System CLR Types dla programu SQL Server 2014 (x64 i x86)**|Ten pakiet instaluje program Microsoft System CLR Types dla programu SQL Server 2014 dla x64 lub x86.|
|**SQL Server 2008 R2 Express**|Ten pakiet instaluje program Microsoft SQL Server 2008 R2 Express, bezpłatna wersja programu Microsoft SQL Server 2008 R2, idealne bazy danych dla małych sieci web, serwera lub aplikacje. Może służyć bezpłatnie do prac deweloperskich i produkcji.|
|**SQL Server 2012 Express**|Ten pakiet instaluje program Microsoft SQL Server 2012 Express.|
|**SQL Server 2012 Express LocalDB**|Ten pakiet instaluje program Microsoft SQL Server 2012 Express LocalDB.|
|**Bibliotek języka Visual C++ Runtime "14" (ARM)**|Ten pakiet instaluje program Visual C++ środowiska wykonawczego biblioteki dla architektury Itanium, które zapewniają procedury programowania w języku systemu operacyjnego Microsoft Windows. Te procedury zautomatyzować wiele typowych zadań programowania, które nie są dostarczane przez języków C i C++.<br /><br /> Aby uzyskać więcej informacji, zobacz [odwołanie do biblioteki C Run-Time](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Visual C++ "14" środowiska uruchomieniowego bibliotek (x64)**|Ten pakiet instaluje biblioteki wykonawcze języka Visual C++ dla x64 systemów, które zawierają procedury programowania dla systemu operacyjnego Microsoft Windows. Te procedury zautomatyzować wiele typowych zadań programowania, które nie są dostarczane przez języków C i C++.<br /><br /> Aby uzyskać więcej informacji, zobacz [odwołanie do biblioteki C Run-Time](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Visual C++ "14" środowiska uruchomieniowego bibliotek (x86)**|Ten pakiet instaluje biblioteki wykonawcze języka Visual C++ dla x86 systemów, które zawierają procedury programowania dla systemu operacyjnego Microsoft Windows. Te procedury zautomatyzować wiele typowych zadań programowania, które nie są dostarczane przez języków C i C++.<br /><br /> Aby uzyskać więcej informacji, zobacz [odwołanie do biblioteki C Run-Time](/cpp/c-runtime-library/c-run-time-library-reference).|

## <a name="see-also"></a>Zobacz także

- [Strona publikowania, Projektant projektu](../../ide/reference/publish-page-project-designer.md)
- [Wstępnie wymagane składniki wdrażania aplikacji](../../deployment/application-deployment-prerequisites.md)
- [Wdrażanie wstępnie wymaganych składników dla aplikacji 64-bitowych](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Wielowersyjność kodu w programie Visual Studio ― przegląd](../../ide/visual-studio-multi-targeting-overview.md)