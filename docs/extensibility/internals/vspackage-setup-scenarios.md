---
title: Scenariusze instalacji pakiet VSPackage | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b58400330bb2032354d28a7b76729a5d7f85fd3c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148993"
---
# <a name="vspackage-setup-scenarios"></a>Scenariusze instalacji pakiet VSPackage

Należy projektować Instalatorem pakiet VSPackage elastyczność. Na przykład konieczne może być w przyszłości wersji poprawkę zabezpieczeń lub strategii biznesowej, która wymaga obsługi dokładnej wersji side-by-side mogą ulec zmianie.

W [obsługi wielu wersji programu Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), możesz przeczytać o zaletach i problemów obsługi instalacji side-by-side [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] z udostępnionym lub side-by-side instalacje VSPackage. Krótko mówiąc, VSPackages side-by-side zapewniają większą elastyczność do obsługi nowych funkcji programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

Scenariuszach opisanych w tym temacie nie są tylko opcje, ale są one widoczne jako sugerowane najlepszych rozwiązań.

## <a name="components-privacy-and-sharing"></a>Składniki, ochrony prywatności i udostępniania

### <a name="make-your-components-independent"></a>Wprowadź składniki niezależne

Po identyfikacji i wypełnić składnika, Przypisz `GUID`i wdrożyć składnik, nie można zmienić jego kompozycji. W przypadku zmiany kompozycji składnika, wynikowy składnik musi być nowy składnik o nowe `GUID`. Biorąc pod uwagę następujące fakty, największą elastyczność versioning jest udostępnianych przez tworzenie jednostki niezależne, samodzielnego każdego składnika. Aby uzyskać więcej informacji na temat zasady składników, zobacz [zmiana kodu składnika](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) i [co się stanie, jeśli składnik reguły są dzielone?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Niemieszanie zasobów udostępnionych i prywatnych w składniku

Liczenie odwołań występuje na poziomie składnika. W rezultacie łączenie zasobów udostępnionych i prywatnych w jednym ze składników uniemożliwia aktualizacji zasobów prywatnych, takich jak plik wykonywalny bez również zastępowania zasobów udostępnionych. W tym scenariuszu tworzy problemy dotyczące zgodności z poprzednimi wersjami i ogranicza możliwość side-by-side tworzenia.

Na przykład wartości rejestru są używane do rejestrowania VSPackage z [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] powinny być utrzymywane w składniku niezależnie od jednego używany do rejestrowania VSPackage z programem Visual Studio. Udostępnione pliki lub wartości rejestru przejdź w jeszcze inny składnik.

## <a name="scenario-1-shared-vspackage"></a>Scenariusz 1: Udostępniony pakiet VSPackage

W tym scenariuszu udostępniony pakiet VSPackage (jedną wartość binarną, która obsługuje wiele wersji programu Visual Studio jest dostarczany w pakiecie Instalatora Windows. Rejestrowanie w każdej wersji programu Visual Studio jest kontrolowana przez funkcje wybierane przez użytkownika. Oznacza to również, że po przypisaniu do oddzielania funkcji, każdego składnika można wybrać indywidualnie do instalowania lub odinstalowywania, zapewnieniem użytkownikowi kontroli integracji pakiet VSPackage różne wersje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. (Zobacz [funkcje Instalatora Windows](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) uzyskać więcej informacji dotyczących używania funkcji pakietów Instalatora Windows.)

![Instalator udostępniony pakiet VSPackage VS](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Jak pokazano na rysunku, udostępniane składniki są nawiązywane część funkcji Feat_Common, która jest zawsze instalowany. Przez włączenie funkcji Feat_VS2002 i Feat_VS2003 widoczności, użytkownicy mogą wybierać w czasie instalacji w wersjach programu Visual Studio mają pakiet VSPackage do integracji. Użytkownicy mogą również używać trybu konserwacji Instalatora systemu Windows do dodawania lub usuwania funkcji, które w tym przypadku dodaje lub usuwa informacje rejestracyjne pakiet VSPackage z różnych wersji programu Visual Studio.

> [!NOTE]
> Ustawienie funkcji wyświetlania kolumny wartości 0 powoduje ukrycie go. Wartość niskiego poziomu kolumny, na przykład 1, gwarantuje, że zawsze zostanie ona zainstalowana. Aby uzyskać więcej informacji, zobacz [właściwości INSTALLLEVEL](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) i [tabeli funkcji](http://msdn.microsoft.com/library/aa368585.aspx).

## <a name="scenario-2-shared-vspackage-update"></a>Scenariusz 2: Udostępniony pakiet VSPackage aktualizacji

W tym scenariuszu jest dostarczany zaktualizowaną wersję Instalatora pakiet VSPackage w scenariuszu 1. Ze względu na dyskusję aktualizacja dodaje obsługę dla programu Visual Studio, ale można również być łatwiejsze poprawki zabezpieczeń lub poprawek usterek z dodatkiem Service pack. Instalowanie składników nowszej zasady Instalatora Windows wymagają, że niezmienione składników już w systemie nie zostaną ponownie skopiowane. W takim przypadku system w wersji 1.0 już zastąpić zaktualizowanego składnika Comp_MyVSPackage.dll i umożliwić użytkownikom możliwość dodania nowej funkcji Feat_VS2005 za jego pomocą składnika Comp_VS2005_Reg.

> [!CAUTION]
> Zawsze, gdy pakiet VSPackage są współużytkowane przez wielu wersji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], jest to, że kolejnych wersjach pakiet VSPackage zachować zgodność z poprzednimi wersjami we wcześniejszych wersjach programu Visual Studio. W przypadku, gdy nie można zachować zgodności z poprzednimi wersjami, należy użyć VSPackages side-by-side, prywatnego. Aby uzyskać więcej informacji, zobacz [obsługi wielu wersji programu Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![Instalator udostępnionych VS pakiet aktualizacji programu VS](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Ten scenariusz przedstawia informacje o nowym Instalatorem pakiet VSPackage obsługi Instalatora systemu Windows dla niewielkie uaktualnienia. Użytkownicy po prostu zainstaluj wersję 1.1 i uaktualni ona w wersji 1.0. Jednak nie jest konieczne w wersji 1.0 w systemie. Tym samym Instalator zainstaluje wersji 1.1 w systemie bez wersji 1.0. Zaletą zapewnienie niewielkie uaktualnienia w ten sposób jest, że nie jest konieczne podąża pracy powstania uaktualnienia Instalatora i Instalator pełnej produktu. Jeden Instalator wykonuje obu zadań. Poprawka zabezpieczeń lub usługi pakietu może zamiast korzystać z poprawek Instalatora Windows. Aby uzyskać więcej informacji, zobacz [Patching i uaktualnień](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).

## <a name="scenario-3-side-by-side-vspackage"></a>Scenariusz 3: Pakiet VSPackage Side-by-Side

Ten scenariusz przedstawia dwa instalatorów pakiet VSPackage — po jednej dla każdej wersji programu Visual Studio .NET 2003 i Visual Studio. Każdy Instalator instaluje side-by-side lub prywatny, pakiet VSPackage (jeden, w szczególności zbudowany i zainstalowany dla określonej wersji programu Visual Studio). Każdy pakiet VSPackage znajduje się w jego własnej składnika. W rezultacie każdy może być indywidualnie obsługiwany poprawki lub konserwacji zwalnia. Ponieważ DLL pakiet VSPackage jest teraz określonej wersji, jest bezpieczne zawierają swoje informacje rejestracyjne w tej samej składnika jako biblioteki DLL.

![Instalator pakietu VS Side-by-Side VS](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Każdy Instalator zawiera także kod, który jest współużytkowana przez dwa pliki instalacyjne. Po zainstalowaniu udostępnionego kodu do wspólnej lokalizacji instalowanie plików msi, zarówno zainstaluje udostępnionego kodu tylko raz. Drugi Instalatora po prostu zwiększa licznika odwołań dla składnika. Liczba odwołań gwarantuje, że jeśli jeden z VSPackages zostanie odinstalowany, udostępniony kod będzie dla innych pakiet VSPackage. Drugi pakiet VSPackage odinstalowanie spowoduje także udostępnionego kodu zostaną usunięte.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Scenariusz 4: Side-by-Side pakiet VSPackage aktualizacji

W tym scenariuszu odniesionej VSPackage dla programu Visual Studio z luki w zabezpieczeniach i należy do wydania aktualizacji. Jak w scenariuszu 2 można utworzyć nowego pliku msi, która aktualizuje istniejącą instalację poprawkę zabezpieczeń, jak również wdrażanie nowych instalacji poprawki zabezpieczeń już na miejscu.

W takim przypadku pakiet VSPackage jest zarządzany pakiet VSPackage zainstalowany w globalnej pamięci podręcznej zestawów (GAC). Należy odtworzyć do poprawkę zabezpieczeń, należy zmienić numer poprawki część numeru wersji zestawu. Informacje o rejestracji dla nowego numeru wersji zestawu spowoduje zastąpienie poprzedniej wersji, co powoduje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] można załadować zestawu stałym.

![Instalator aktualizacji pakietu VS Side-by-Side VS](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Aby uzyskać więcej informacji dotyczących wdrażania zestawów side-by-side, zobacz [uprościć wdrażanie i rozwiązywania piekłem bibliotek DLL z programu .NET Framework](http://msdn.microsoft.com/library/ms973843.aspx).

## <a name="see-also"></a>Zobacz też

[Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)  
[Obsługiwanie wielu wersji programu Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)