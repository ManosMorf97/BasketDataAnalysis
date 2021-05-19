Θα υπάρχουν αναβαθμίσεις ανά τακτά χρονικά διαστήματα 
# BasketDataAnalysis
Tα δεδομένα ειναι από [εδώ](https://www.kaggle.com/andrewsundberg/college-basketball-dataset)

Σε μονιμη βαση   αφαιρούνται τα columns SEEDS και POSTSEASON επειδή στο Dataset πολλες ομάδες δεν είχαν τιμή σε αυτά(ΝΑ).
<br>


Στο αρχείο [requirements.ipynb](https://github.com/ManosMorf97/BasketDataAnalysis/blob/master/requirements.ipynb) βρίσκεται 
ο κώδικας που έχει να κάνει με τις απαιτήσεις της πτυχιακής μου.

Στο αρχείο [Περιγραφή.pdf](https://github.com/ManosMorf97/BasketDataAnalysis/blob/master/%CE%A0%CE%B5%CF%81%CE%B9%CE%B3%CF%81%CE%B1%CF%86%CE%AE.pdf) βρίσκεται η περιγραφή της πτυχιακής μου.
<br>
## Ότι ακολουθεί παρακάτω δεν έχουν να κάνουν με την πτυχιακή μου.Είναι εντελώς δικά μου
<br>
<br>
Αρχικα αφαίρεσα τα column ΥΕΑR,CONF και WAB.<br>
Kαι αποφάσισα να χρησιμοποιήσω το column BARTHAG ως μεταβλητή εξόδου και να δω πόσο καλές προβλεψεις γίνονται.
<br>

Στα αρχεία [Untitled1.ipynb](https://github.com/ManosMorf97/BasketDataAnalysis/blob/master/Untitled1.ipynb) και

[Untitled2.ipynb](https://github.com/ManosMorf97/BasketDataAnalysis/blob/master/Untitled2.ipynb)(κυρίως)

μπορείτε να δείτε την πρόοδο μου σχετικά με Basketball_datasets
<br>
Επειδή η διάσπαση των δεδομένων για train και test γίνεται με τυχαίο τρόπο έτρεξα 10 φορές τον αλγόριθμο με σκοπό να παρατηρήσω την συμπριφορά.Επειτα μείωσα τους νευρώνες στους 400 και ο Μέσος Ωρος στο score φάνηκε πολύ καλύτερος
<br>
<br>
Yστερα δωκίμασα να δω τι γίνεται αν χρησιμοποιήσω το column CONF ως μεταβλητή εξόδου και παρατήρησα ότι δεν υπάρχει συσχέτιση με τον CONF
καθως αν αφαιρεσω 200 νευρωνες παρατήρησα μεγάλη παρακμή στο score και όταν πρόσθεσα 400 παρατήρησα πολύ μικρή άνοδο
<br>
<br>
Mια άλλη καινοτομία που πήγα να εφαρμόσω είναι να χρησιμοποιήσω είναι να δω τι θα γίνει αν χρησιμοποιήσω ως μεταβλητή εξόδου το ADJ_Τ(κατοχές ανά αγώνα) αφαιρώντας τα columns TEAM,CONF,BARTHAG και YEAR.Χρησιμοποιώντας και πάλι Νευρωνικά Δίκτυα παρατήρησα πως το score ήταν κάτω του 10% και πολλές φορές αρνητικό. 
Αφαιρώντας περισσότερα columns το άνω φράγμα του score αυξήθηκε αλλά πάλι σε πολλές περιπτώσεις το score ήταν αρνητικό
<br>
<br>
Στη συνέχεια είπα να δωκιμάσω την αρχική μου μέθοδο με το barthag αλλά αυτήν την φορά χρησιμοποίησα το 50% του dataset για εκπαίδευση.<br>Και πάλι παρατήρησα ότι και με αυτό το ποσοστό υπήρχε καλή επίδοση.[Eδώ](https://github.com/ManosMorf97/BasketDataAnalysis/blob/master/Untitled2.ipynb) είναι το αποτέλεσμα.
<br>
Μετά τα δεδομένα για test τα έβαλα 60% και το score είχε μια μικρή κάθοδο
<br><br>
Eπίσης έκανα test με output το Barthag κρατωντας τα columns G(games) και W(wins) για να δω τι συσχέτιση υπάρχει και παρατήρησα παρ όλα αυτά ότι η συσχέτιση ήταν και πάλι μεγάλη
<br><br>
Επειτα ξαναεκπαίδευσα το σύστημα αφαιρώντας τα παραπάνω columns(G,W) και (YEAR,CONF,WAB) και είχα για test το 20% των δεδομένων,επειδή με το 50% το σκορ χαμήλωσε σε εναν μικρό βαθμο(0.15 περίπου) έχωντας απ έξω τα (G,W)
<br><br>
Aκόμη δοκίμασα ως output το WAB αφαιρόντας ΤΕΑΜ,CONF,G,W,BARTHAG, και YEAR και έχοντας το 80% των δεδομένων για εκπαίδευση παρατήρησα οτι το μεσο score ηταν περιπου 82%.
<br>
Eπειδή παρατήρησα πως το score ηταν καλό για τα outputs WAB και BARTHAG είδα την συσχέτιση μεταξύ BARTHAG και WAB με το 50% των δεδομένω για εκπαίδευση με τον αλγόριθμο KNearestNeighbor με τους 5 κοντινότερους γείτονες  και παρατήρησα ότι το μεσο score ήταν περίπου 84%
<br>
<br>
## Συμπεράσματα
Τελικά παρατήρησα πως μπορεί να προβλεπτεί το WAB και το BARTHAG με μικρές αποκλείσεις εκπαιδεύοντας το συστημα με καποια δεδομένα
