# AutoElecto - Preču meklēšana un salīdzināšana

AutoElecto ir Python aplikācija, kas ļauj lietotājam meklēt un salīdzināt preces no divām populārām tīmekļa vietnēm: **lemona.lv** un **aliexpress.com**. Pēc pieprasījuma lietotājam tiek rādīts saraksts ar preču nosaukumiem, cenām, veikalu nosaukumiem un saitēm, sakārtoti pēc cenas no augstākās uz zemāko. Aplikācija izmanto **Selenium** tīmekļa automatizācijai un ātru **Quick Sort** algoritmu, lai kārtotu atrastās preces.

## Funkcionalitāte

- Lietotājs ievada preces nosaukumu.
- Sistēma meklē preces divās vietnēs: **lemona.lv** un **aliexpress.com**.
- Pirmajā lapā tiek analizēti līdz 80 produktiem no katras vietnes.
- Rezultāti tiek sakārtoti pēc cenas no augstākās uz zemāko, izmantojot **Quick Sort** algoritmu.
- Lietotājs var izvēlēties, vai skatīt tikai vienu veikalu (lemona.lv vai aliexpress.com), vai abus.

## Instalēšana

1. Lejupielādējiet vai klonējiet šo repozitoriju:

   ```bash
   git clone https://github.com/TavsGitHubVards/AutoElecto.gi
