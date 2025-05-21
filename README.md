# AutoElecto - Preču meklēšana un salīdzināšana

**AutoElecto** ir Python skripts, kas ļauj lietotājiem pieprasīt preces, ko viņi vēlas atrast divās tīmekļa vietnēs: **lemona.lv** un **aliexpress.com**. Sistēma analizē abu vietņu pirmās lapas, salīdzina preču cenas un izvada sarakstu ar katras atrastās preces veikalu, nosaukumu, cenu un saiti, sakārtotu pēc cenas no augstākās uz zemāko. Tāpat sistēma ļauj lietotājam izvēlēties, kuru no šiem diviem veikaliem viņš vēlas izmantot.

## Funkcionalitāte

- Lietotājs ievada preces nosaukumu.
- Meklēšana tiek veikta abās vietnēs: **lemona.lv** un **aliexpress.com**.
- Sistēma analizē preces no abām vietnēm, ņemot vērā, ka katrā lapā tiek rādītas līdz 80 preces (lemona.lv vietnē ir iespējams mainīt šo skaitu).
- Tiek izmantota ātra **Quick Sort** metode, lai sakārtotu atrastās preces pēc cenas, sākot no augstākās līdz zemākajai.
- Lietotājs tiek aicināts izvēlēties, kuru veikalu viņš vēlas apskatīt: tikai **lemona.lv**, tikai **aliexpress.com**, vai abus.
- Programma izvada sarakstu ar preces nosaukumu, veikalu nosaukumu, cenu un saiti uz preci.

## Tehnoloģijas un pieejas

- **Selenium**: automatizē pārlūkošanas darbības un datu iegūšanu no tīmekļa vietnēm.
- **Quick Sort**: ātrā kārtošanas metode, kas tiek izmantota, lai ātri sakārtotu produktus pēc cenas, izmantojot rekursiju.
- **Datu struktūra**: Katra prece tiek glabāta savā struktūrā, izmantojot **Product** klasi, kas ietver informāciju par preces nosaukumu, cenu un veikalu.
