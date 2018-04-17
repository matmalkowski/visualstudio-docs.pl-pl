---
title: Opracuj kodu w programie Visual Studio bez projekty i rozwiązania | Dokumentacja firmy Microsoft
ms.date: 02/21/2018
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 082e64d80080eec48c311254461b85812a969841
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Opracuj kodu w programie Visual Studio bez projektów i rozwiązań

W Visual Studio 2017 r możesz otworzyć kodu z niemal dowolnego typu na podstawie katalogu projektu do programu Visual Studio bez konieczności plik rozwiązania lub projektu. Oznacza to, można, na przykład klonowanie repozytorium w usłudze GitHub, otwórz go bezpośrednio w programie Visual Studio i rozpocząć tworzenie bez konieczności tworzenia rozwiązania lub projektu. W razie potrzeby można określić zadania niestandardowej kompilacji i uruchomić parametrów za pomocą prostego pliki w formacie JSON.

Po otwarciu plików kodu programu Visual Studio **Eksploratora rozwiązań** Wyświetla wszystkie pliki w folderze. Możesz kliknąć dowolny plik, aby rozpocząć edycji. W tle Visual Studio rozpoczyna indeksowania pliki, aby włączyć IntelliSense, nawigacji i funkcje refaktoryzacji. Jak edytować, tworzenie, przenoszenie i usuwania plików programu Visual Studio automatycznie śledzenia zmian i stale aktualizuje jego indeks IntelliSense. Kod będzie wyświetlany z kolorowanie składni, a w wielu przypadkach obejmują podstawowe instrukcji IntelliSense.

## <a name="open-any-code"></a>Otwórz każdy kod

Kod do programu Visual Studio można otworzyć w dowolnym z następujących sposobów:

- Na pasku menu programu Visual Studio wybierz **pliku** > **Otwórz** > **folderu**, a następnie przejdź do lokalizacji kodu.
- W menu kontekstowym (kliknij prawym przyciskiem myszy) do folderu zawierającego kod, wybierz **Otwórz w programie Visual Studio** polecenia.
- Wybierz **Otwórz Folder** łącza w programie Visual Studio **— strona początkowa**.
- Jeśli jesteś użytkownikiem klawiatury, naciśnij klawisz **Ctrl**+**Shift**+**Alt**+**O** w języku Visual Studio.
- Otwórz kod z sklonowanego repozytorium GitHub.

### <a name="to-open-code-from-a-cloned-github-repo"></a>Aby otworzyć kodu z sklonowanego repozytorium GitHub

Poniższy przykład pokazuje, jak można sklonować repozytorium GitHub, a następnie otwórz jego kodu w programie Visual Studio. Aby wykonać tę procedurę, musi mieć konto usługi GitHub i Git dla systemu Windows zainstalowanych w systemie. Zobacz [utworzeniem nowego konta usługi GitHub](https://help.github.com/articles/signing-up-for-a-new-github-account/) i [Git dla systemu Windows](https://git-for-windows.github.io/) Aby uzyskać więcej informacji.

1. Przejdź do repozytorium, które chcesz sklonować w witrynie GitHub.

1. Wybierz **klonowania lub pobrać** przycisk, a następnie wybierz pozycję **Kopiuj do Schowka** przycisk w menu rozwijanym, aby skopiować bezpiecznego adresu URL dla repozytorium GitHub.

   ![Przycisk powielania GitHub](./media/VSIDE_Code_Clone.png)

1. W programie Visual Studio, wybierz **Team Explorer** kartę, aby otworzyć **Team Explorer**. Jeśli karta nie jest widoczna, otwórz go z **widoku** > **Team Explorer**.

1. W programie Team Explorer w obszarze **lokalnego repozytoriów Git** wybierz **klonowania** polecenia, a następnie wklej adres URL strony GitHub w polu tekstowym.

   ![Klonowanie projektu](./media/VSIDE_Code_Clone2.png)

1. Wybierz **klonowania** przycisk sklonować pliki projektu do lokalnego repozytorium Git. W zależności od rozmiaru repozytorium ten proces może potrwać kilka minut.

1. Po repozytorium ma został sklonowany w systemie, w **Team Explorer**, wybierz **Otwórz** polecenia w menu kontekstowym (kliknij prawym przyciskiem myszy) nowo sklonowanego repozytorium.

   ![Sklonowanego repozytorium](./media/VSIDE_Code_Clone3.png)

1. Wybierz **Pokaż widok folderu** polecenie, aby wyświetlić pliki w **Eksploratora rozwiązań**.

   ![Pokaż widok folderu](./media/VSIDE_Code_Clone3_show.png)

   Można teraz przeglądanie folderów i plików w repozytorium sklonowany i wyświetlić i wyszukiwanie kodu w edytorze kodu programu Visual Studio z kolorowanie składni i inne funkcje.

|         |         |
|---------|---------|
|  ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo")|    [Obejrzyj film](https://mva.microsoft.com/en-us/training-courses/getting-started-with-visual-studio-2017-17798?l=lp3TOKD6D_6711787171) dotyczące klonowania i otworzyć kodu z repozytorium GitHub, w programie Visual Studio. |

## <a name="run-and-debug-your-code"></a>Uruchom i debugowanie kodu

Można debugować kodu w programie Visual Studio bez projekt lub rozwiązanie! Aby debugować niektórych języków, konieczne może być Określ prawidłowe *uruchamiania pliku* w codebase, takich jak skrypt, plik wykonywalny lub projektu. Pole listy rozwijanej obok pola **Start** przycisk na pasku narzędzi zawiera wszystkie wykryte Visual Studio, a także szczegółowo określić elementy elementy startowe. Visual Studio działa ten kod najpierw podczas debugowania kodu.

Konfigurowanie kodu do uruchomienia w programie Visual Studio zależy od tego, jakiego rodzaju kodu jest, i jakie narzędzia kompilacji.

### <a name="codebases-that-use-msbuild"></a>Codebases używające programu MSBuild

Na podstawie MSBuild codebases może mieć wielu konfiguracji kompilacji, które są widoczne w **Start** przycisku listy rozwijanej. Wybierz plik, który ma być używany jako element startowy, a następnie wybierz pozycję **Start** przycisk, aby rozpocząć debugowanie.

> [!NOTE]
> Dla języka C# i Visual Basic codebases, musisz mieć **tworzenia klasycznych aplikacji .NET** obciążenia zainstalowane. Dla języka C++ codebases, musisz mieć **tworzenia klasycznych aplikacji w języku C++** obciążenia zainstalowane.

### <a name="codebases-that-use-custom-build-tools"></a>Codebases tego użycia niestandardowych narzędzi kompilacji

Jeśli używany przez codebase niestandardowych narzędzi kompilacji, a następnie programu Visual Studio należy wskazać sposób tworzenia przy użyciu kodu *zadania kompilacji* które są zdefiniowane w *JSON* pliku. Aby uzyskać więcej informacji, zobacz [Dostosowywanie kompilacji i debugowanie zadań](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

### <a name="codebases-that-contain-python-or-javascript-code"></a>Codebases, który zawiera kod języka Python lub JavaScript

Jeżeli baza kodu zawiera kod języka Python lub JavaScript, nie trzeba skonfigurować dowolne *JSON* pliki, ale trzeba instalować odpowiednie obciążenie. Należy także skonfigurować skrypt uruchamiania:

1. Zainstaluj [programowanie Node.js](https://www.visualstudio.com/vs/node-js/) lub [programowania Python](https://www.visualstudio.com/vs/python/) obciążenie, wybierając **narzędzia** > **Pobierz narzędzia i funkcje...** , lub zamknięcia programu Visual Studio i uruchamiając Instalator programu Visual Studio.

   ![Node.js i Python obciążeń programowanie](media/python_nodejs_workloads.png)

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy lub kontekstu menu plik JavaScript lub Python, wybierz **Ustaw jako element startowy** polecenia.

1. Wybierz **Start** przycisk, aby rozpocząć debugowanie.

### <a name="codebases-that-contain-c-code"></a>Codebases, który zawiera kod w języku C++

Aby dowiedzieć się, jak otwieranie kod w języku C++ bez rozwiązań lub projektów programu Visual Studio, zobacz [Otwórz Folder projektów C++](/cpp/ide/non-msbuild-projects).

### <a name="codebases-that-contain-a-visual-studio-project"></a>Codebases zawierających projektu programu Visual Studio

Jeśli folder kod zawiera projektu programu Visual Studio, możesz wyznaczyć projektu jako element startowy.

![Ustaw projekt jako element startowy](media/customize-set-project-as-startup-item.png)

**Start** przycisku zmiany tekstu w celu odzwierciedlenia, że projekt jest element startowy.

![Projekt na przycisku Start](media/customize-start-button-project.png)

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie kompilacji i debugowanie zadań](../ide/customize-build-and-debug-tasks-in-visual-studio.md)
- [Otwórz Folder projektów dla języka C++](/cpp/ide/non-msbuild-projects)
- [CMake projektów w języku C++](/cpp/ide/cmake-tools-for-visual-cpp)
- [Pisanie kodu w edytorze kodu i tekstu](../ide/writing-code-in-the-code-and-text-editor.md)