ΑΡΙΣΤΟΤΕΛΕΙΟ ΠΑΝΕΠΙΣΤΗΜΙΟ ΘΕΣΣΑΛΟΝΙΚΗΣ

ΠΟΛΥΤΕΧΝΙΚΗ ΣΧΟΛΗ

ΤΜΗΜΑ ΗΛΕΚΤΡΟΛΟΓΩΝ ΜΗΧΑΝΙΚΩΝ &amp; ΜΗΧΑΝΙΚΩΝ ΥΠΟΛΟΓΙΣΤΩΝ

# Αρχιτεκτονική Προηγμένων Υπολογιστών - 3η Εργαστηριακή Άσκηση

# Βήμα 1
## Απάντηση ερώτησης 1

Ως dynamic power αναφέρεται η ισχύς που καταναλώνεται από το άνοιγμα και κλείσιμο
των transistors, η οποία επηρεάζεται από το πρόγραμμα που τρέχει κάθε φορά, ενώ το
leakage είναι η κατανάλωση της ισχύος που οφείλεται στο ρεύμα διαρροής των
transistor, το οποίο οφείλεται σε φυσικά αίτια και η αντίστοιχη κατανάλωση ισχύος
είναι σταθερή για μια δεδομένη τιμή τάσης τροφοδοσίας (στατική ισχύς) [1].
Με άλλα λόγια, το leakage θα ήταν η τιμή ισχύος του επεξεργαστή αν δεν έτρεχε κανένα
απολύτως πρόγραμμα και ήταν απλά συνδεδεμένος στο ρεύμα. Αυτό που επηράζει το
leakage είναι τα ίδια τα transistors, συγκεκριμένα η τάση τροφοδοσίας και το μέγεθος τους.

Για διαφορετικά προγράμματα στον ίδιο επεξεργαστή, το μέγεθος που θα επηρεαστεί
είναι το dynamic power και εξαρτάται από το πόσα και ποια μέρη του επεξεργαστή
θα χρησιμοποιηθούν, ανάλογα με τις απαιτήσεις του εκάστοτε προγράμματος.

Ο χρόνος εκτέλεσης κάθε προγράμματος δεν επηρεάζει το dynamic power, το
οποίο εξαρτάται αποκλειστικά από τη χωρητικότητα της πύλης των transistor, την
τάση της πηγής και τη συχνότητα αλλαγής (switching frequency) [2]. Ο χρόνος
εκτέλεσης επηρεάζει μόνο τη συνολική κατανάλωση **ενέργειας** σε Joule. Προφανώς,
μεγαλύτερος χρόνος εκτέλεσης σημαίνει περισσότερη κατανάλωση **ενέργειας**, όχι όμως ισχύος.

## Απάντηση ερώτησης 2

Η διάρκεια της μπαταρίας, δηλαδή η συνολική κατανάλωση ενέργειας, επηρεάζεται από
τα static power (leakage), dynamic power και τον χρόνο εκτέλεσης. Αν ο πρώτος επεξεργαστής
που καταναλώνει 4W, καταναλώνει 2W σε dynamic και 2W σε leakage, ενώ ο δεύτερος, των
40 W, καταναλώνει 39.9W σε dynamic και 0.1W σε leakage, τότε αν ο δεύτερος τρέχει πιο
γρήγορα, είναι πιθανό να έχει μεγαλύτερη διάρκεια μπαταρίας. Συνεπώς, μπορούμε να
συνάγουμε το συμπέρασμα οτι τα δεδομένα που μας δίνει ο mcpat, δεν είναι αρκετά
για να υπολογίσουμε τη συνολική κατανάλωση ενέργειας, καθώς χρειαζόμαστε τον χρόνο
εκτέλεσης του προγράμματος. Σε αυτό μπορούν να βοηθήσουν προσομοιωτές όπως ο gem5,
αν τον τρέξουμε παράλληλα με τον mcpat, για το ίδιο πρόγραμμα.

## Απάντηση ερώτησης 3

Το συνολικό leakage power του Xeon είναι 100 φορές μεγαλύτερο από το αντίστοιχο του A9,
το οποίο σημαίνει ότι ο Xeon θα καταναλώνει περισσότερη ισχύ σε κατάσταση αδράνειας
από τον A9, εφόσον είναι μόνο 40 φορές πιο γρήγορος. Αυτά ισχύουν, με την υπόθεση ότι
το σύστημα συνεχίζει να τρέχει, μετά την ολοκλήρωση της εκτέλεσης του προγράμματος
(μένει σε κατάσταση αδράνειας).

# Βήμα 2


## Απάντηση ερώτησης 1

Το EDP υπολογίστηκε για κάθε benchmark και configuration του επεξεργαστή ως το
γινόμενο του συνολικού power (runtime dynamic + gate leakage + subthreshold leakage)
με το χρόνο εκτέλεσης του κάθε benchmark (`sim_seconds`). Τα αποτελέσματα παρουσιάζονται
στον παρακάτω πίνακα με ακρίβεια τεσσάρων δεκαδικών ψηφίων. Τα πλήρη δεδομένα μπορούν
να βρεθούν στο αρχείο `benchmark-name-edp.csv` που βρίσκεται στο φάκελο `graphs/benchmark-name`.

|     Case name    | EDP (specbzip) | EDP (spechmmer) | EDP (speclibm) | EDP (specmcf) | EDP (specsjeng) | Average EDP |
|:----------------:|:--------------:|:---------------:|:--------------:|:-------------:|:---------------:|:-----------:|
| Default MinorCPU |     0.1211     |      0.0863     |     0.2245     |     0.0923    |      0.6288     |    0.2306   |
|   64k L1i size   |     0.1525     |      0.1115     |     0.2948     |     0.1198    |      0.5548     |   0.24668   |
|  4-way L1i assoc |     0.1252     |      0.0922     |     0.2383     |     0.0877    |      0.6697     |   0.24262   |
|  8-way L1i assoc |     0.1289     |      0.0948     |     0.2460     |     0.0903    |      0.6925     |    0.2505   |
|   32k L1d size   |     0.0688     |      0.0489     |     0.1328     |     0.0540    |      0.3861     |   0.13812   |
|   128k L1d size  |     0.1478     |      0.1106     |     0.2835     |     0.1162    |      0.7920     |   0.29002   |
|  4-way L1d assoc |     0.0950     |      0.0709     |     0.1768     |     0.0748    |      0.4914     |   0.18178   |
|  8-way L1d assoc |     0.1031     |      0.0769     |     0.1891     |     0.0823    |      0.5335     |   0.19698   |
|    1MB L2 size   |     0.1230     |      0.0873     |     0.2239     |     0.0920    |      0.6263     |    0.2305   |
|    4MB L2 size   |     0.1198     |      0.0878     |     0.2256     |     0.0930    |      0.6328     |    0.2318   |
|  2-way L2 assoc  |     0.1212     |      0.0875     |     0.2245     |     0.0923    |      0.6287     |   0.23084   |
|  4-way L2 assoc  |     0.1209     |      0.0875     |     0.2245     |     0.0923    |      0.6286     |   0.23076   |
|   32b line size  |     0.0860     |      0.0595     |     0.2439     |     0.0618    |      0.7453     |    0.2393   |
|  128b line size  |     0.1504     |      0.1066     |     0.2060     |     0.1190    |      0.5117     |   0.21874   |
|  256b line size  |     0.2995     |      0.2103     |     0.3285     |     0.2343    |      0.8205     |   0.37862   |
|   256k L1d size  |     0.1724     |      0.1472     |     0.3297     |     0.1380    |      0.9200     |   0.34146   |
|    Optimal CPI   |     0.2014     |      0.1507     |     0.3301     |     0.0787    |      1.1043     |   0.37304   |

Παρατηρούμε λοιπόν ότι η βέλτιστη επιλογή όσον αφορά την κατανάλωση ενέργειας για όλα
τα benchmarks είναι η μείωση της data cache σε 32kB από τα αρχικά 64.
Επιπρόσθετα, η κατανάλωση ενέργειας θα μπορούσε να μειωθεί περαιτέρω ανάλογα με το
υπολογιστικό φορτίο του κάθε benchmark. Συγκεκριμένα, θα μπορούσε να μειωθεί και το
μέγεθος γραμμής από 64 σε 32 bytes για τα `specbzip`, `spechmmer` και `specmcf`,
ενώ για τα `specsjeng` και `speclibm` να αυξηθεί το associativity της L1 data cache
από 2-way σε 4-way.

## Απάντηση ερώτησης 2 - Γραφήματα peak power

Η μέγιστη (peak) ισχύς για κάθε περίπτωση απεικονίζεται στα παρακάτω διαγράμματα,
χωρισμένη ανά benchmark. Η κόκκινη γραμμή δείχνει την ισχύ που καταγράφηκε για την
περίπτωση του `MinorCPU` χωρίς καμία μεταβολή στα χαρακτηριστικά του (2GHz clock,
32kB 2-way L1 inst. cache, 64kB 2-way L1 data cache, 2MB 8-way L2 cache,
64 byte cache line).

### specbzip
![specbzip-pp](./graphs/specbzip/specbzip-peak.png)
### spechmmer
![spechmmer-pp](./graphs/spechmmer/spechmmer-peak.png)
### speclibm
![speclibm-pp](./graphs/speclibm/speclibm-peak.png)
### specmcf
![specmcf-pp](./graphs/specmcf/specmcf-peak.png)
### specsjeng
![specsjeng-pp](./graphs/specsjeng/specsjeng-peak.png)

Παρατηρούμε λοιπόν ότι το peak power επηρεάζεται μόνο από τις διαφορετικές επιλογές
σε cache size, associativity κλπ. για κάθε επεξεργαστή, και δεν διαφέρει ανάλογα με
τον υπολογιστικό φόρτο κάθε benchmark.
Από τα γραφήματα φαίνεται ότι τη μεγαλύτερη επιρροή στο τελικό peak power
έχει το μέγεθος γραμμής της cache, με 27.2066 W για τη μεγαλύτερη επιλογή των 256 byte
(η μεγαλύτερη κατανάλωση συνολικά) και 2.2259 W για τη μικρότερη επιλογή των 32 byte
(η οποία έχει και τη μικρότερη κατανάλωση συνολικά). Η κατανάλωση επηρεάζεται και από
το μέγεθος της L1 cache, και μάλιστα φαίνεται πως τουλάχιστον για την data cache ο ρυθμός
αύξησης σε κάθε διπλασιασμό του μεγέθους δεν είναι γραμμικός και μάλιστα φθίνει όσο το
μέγεθος αυξάνεται, όπως στον ακόλουθο πίνακα:

| Μετάβαση (L1 data cache) | Διαφορά |
|--------------------------|---------|
| 32->64kB                 | +0.8663 |
| 64->128kB                | +0.5127 |
| 128->256kB               | +0.3683 |

Τη μικρότερη επιρροή όλων έχει το associativity στις L1 και L2 caches καθώς και το
μέγεθος της L2 cache. Το μέγεθος της L2 δεν επηρεάζει την κατανάλωση στον ίδιο βαθμό
με αυτόν της L1 λόγω του ότι η L2, αν και μεγαλύτερη που θα συνεπαγόταν περισσότερο
χρόνο (άρα και ενέργεια) για lookups σε περίπτωση που της ζητηθεί κάτι, δεν παύει να
είναι η cache η οποία ενεργοποιείται όταν η L1 έχει miss, και για μικρά L1 miss rates
η L2 δεν έχει μεγάλο αριθμό αιτήσεων. Με άλλα λόγια, μακροχρόνια η L2 ακόμα κι αν
είναι λόγω μεγέθους πιο ενεργοβόρα ανά lookup από την L1, δεν δέχεται τον ίδιο αριθμό
αιτήσεων, με αποτέλεσμα το ενεργειακό κόστος να "επιμερίζεται" στο μεγαλύτερο χρονικό
διάστημα.


## Πιθανές αιτίες σφαλμάτων

Ο McPAT δεν κάνει πλήρη προσομοίωση των κυκλωμάτων του επεξεργαστή σε επίπεδο
transistor όπως θα έκανε κάποιος προσομοιωτής mixed-signal (πχ. το SPICE). Μια
πλήρης προσομοίωση όμως με κάποιο εργαλείο όπως το SPICE ναι μεν θα έδινε πολύ
ακριβέστερα αποτελέσματα (ο McPAT έχει απόκλιση 10-20% από τις πραγματικές τιμές
των ζητούμενων metrics, [3] σελ.6-7) αλλά μπορεί να δώσει τιμές πολύ πιο γρήγορα.
Μια ακόμα πιθανή πηγή σφαλμάτων είναι και ο gem5, καθώς κάνει από προεπιλογή μόνο
syscall emulation, αγνοώντας τυχόν καθυστερήσεις οφειλόμενες στο υλικό και ως εκ
τούτου μπορεί να παρουσιάζει λάθη στο χρόνο εκτέλεσης.
Μάλιστα, το μοντέλο `TimingSimpleCPU` μπορεί να περιορίσει ως ένα βαθμό τα λάθη,
καθώς λαμβάνει υπόψη του το timing του υλικού. Ο συνδυασμός των δύο προγραμμάτων
πολλαπλασιάζει τα σφάλματα στις παραγόμενες τιμές, αν δεν γίνεται διόρθωση πριν
τον τελικό υπολογισμό.

## Αξιολόγηση εργασίας



*-Παναγιώτης Σαββίδης*




*-Γρηγόριος Παυλάκης*


[1]: Patterson - Hennessy: Computer Architecture: A Quantitative Approach, 5th ed., σελ. 26
[2]: https://web.archive.org/web/20150812030010/http://download.intel.com/design/network/papers/30117401.pd
[3]: https://www.hpl.hp.com/research/mcpat/micro09.pdf