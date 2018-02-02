# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Klonuj repozytorium kodu języka Python w programie Visual Studio

Po wprowadzeniu [zainstalowany program Visual Studio Tools dla AI](installation.md), można łatwo Klonuj repozytorium kodu Python i utworzyć projekt z niego.

1. Do nawiązania połączenia repozytoriów GitHub, uruchom Instalatora programu Visual Studio wybierz **Modyfikuj**i wybierz **pojedynczych składników** kartę. Przewiń w dół do **kodu narzędzia** zaznacz **rozszerzenie GitHub dla programu Visual Studio**i wybierz **Modyfikuj**.
    
    ![Wybierając rozszerzenie GitHub w Instalatorze programu Visual Studio](media\create-project-repo\installation-github-extension.png)
    
2. Uruchom program Visual Studio.

3. Wybierz **Widok > Team Explorer...**  otworzyć **Team Explorer** okna, w którym można nawiązać połączenia z usługi GitHub lub Visual Studio Team Services lub sklonować repozytorium.

    ![Zespół przedstawiający okno Eksploratora Visual Studio Team Services, GitHub i klonowanie repozytorium](media\create-project-repo\team-explorer.png)

4. W polu adresu URL **lokalnego repozytoria Git**, wprowadź `https://github.com/Microsoft/samples-for-ai`, wprowadź folder plików sklonowany i wybierz **klonowania**.

    > [!Tip]
    > Folder, który określisz w programie Team Explorer jest konkretnego folderu do odbierania sklonowany plików. W przeciwieństwie do `git clone` poleceń, utworzenie klona w programie Team Explorer nie tworzy automatycznie podfolder o nazwie repozytorium.

5. Kiedy klonowanie zostanie ukończone, kliknij dwukrotnie folder repozytorium w dolnej części Team Explorer, aby przejść do pulpitu nawigacyjnego repozytorium. W obszarze **rozwiązań**, wybierz pozycję **nowy...** .

    ![Okno Eksploratora zespołu, tworzenia nowego projektu z klonu](media\create-project-repo\team-explorer-new-project.png)

6. W **nowy projekt** okno dialogowe zostanie wyświetlone, wybierz pozycję "**z istniejącego kodu Python**", określ nazwę dla projektu, ustaw **lokalizacji** do folderu repozytorium, i Wybierz **OK**. W oknie kreatora wybierz **Zakończ**.

7. Wybierz **Widok > Eksploratora rozwiązań** z menu.

8. W Eksploratorze rozwiązań rozwiń `TensorFlow Examples> MNIST` węzła, kliknij prawym przyciskiem myszy `convolutional.py`i wybierz **Ustaw jako plik uruchamiania**. W tym kroku opisano Visual Studio plik, który należy używać, gdy uruchamiania projektu.

10. Naciśnij klawisze Ctrl + F5 lub wybierz **Debuguj > Uruchom bez debugowania** do uruchomienia programu. Jeśli widzisz ", ponownie Sprawdź katalog roboczy ustawienia w poprzednim kroku.


11. Jeśli program zostanie uruchomiony pomyślnie, zobaczysz go uruchom, aby pobrać do szkolenia i przetestować zestawu danych, a następnie nauczenia modelu i Twoje współczynnik błędów wyjścia. Ma współczynnik błędów, aby zmniejszyć wraz z upływem czasu

    ![Pierwsze dane wyjściowe z programu Python MNIST](media\create-project-repo\tensorflow-mnist-running.png)

> Jeśli używasz Anaconda i wystąpi błąd o Brak numpy, może być konieczna zmiana środowiska python, konieczne może być [zmienić środowiska python, aby użyć Anaconda](../python/managing-python-environments-in-visual-studio.md)

11. Można zwizualizować postępu za pomocą TensorBoard. Kliknij prawym przyciskiem myszy projekt i kliknij przycisk **Uruchom TensorBoard** następnie wybierz katalog TensorBoard rejestruje dane wyjściowe.

    ![Uruchom tensorboard](media\create-project-repo\run-tensorboard.png)

11. Zwróć uwagę, błąd zmniejszenie nadgodziny, co oznacza, że jest poprawy jakości

    ![Uruchom tensorboard](media\create-project-repo\tensorboard.png)