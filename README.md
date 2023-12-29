#include <stdio.h>
#include <stdlib.h>
#include <string.h>
void menu(){
    printf("   ** Menu principal ** \n"); 
    printf("      1- Créer un compte \n ");
    printf("      2- Créer une réservation \n ");
    printf("      3- Afficher les détails du bus \n ");
    printf("      4- Afficher et modifier les details d'une réservation \n ");
    printf("      5- Créer un nouveau bus \n ");
    printf("      6- Annuler la réservation ");
    printf("      7- Afficher l'avis du voyageur ");
    printf("      0- Quitter \n ");
}
typedef struct{
    char nom;
    char prenom;
    int age;
    char email;
}Voyageur;
typedef struct{
    int numero_reservation;
    int numero_bus;
    Voyageur voyageur;
    char date;     
}reservation ; 
typedef struct{
    int numero_bus;
    char destination;
    int nbre_places;
    char disponibilite;    
}bus;
typedef struct {
    int numero_reservation;
    char avis[100];
} AvisVoyageur;                
Voyageur creer_compte(){
    Voyageur nouveauvoyageur;
    printf(" Nom du voyageur : ");
    scanf("%s", nouveauvoyageur.nom);
    printf(" Prenom du voyageur : ");
    scanf("%s", nouveauvoyageur.prenom);
    printf(" Age du voyageur : ");
    scanf("%d", &nouveauvoyageur.age);
    printf(" l'adresse email du voyageur : ");
    scanf("%s", nouveauvoyageur.email);
    return nouveauvoyageur;
    printf(" Le Compte du voyageur est créé avec succès !\n");
}
reservation creerReservation(int numero_reservation, int numero_bus,char date) {
    reservation nouvelleReservation;
    nouvelleReservation.numero_reservation = numero_reservation;
    nouvelleReservation.numero_bus = numero_bus;
    nouvelleReservation.date=date;
    nouvelleReservation.voyageur = creer_compte();
    return nouvelleReservation;
    printf("La réservation a été créée avec succès !\n");
}
void afficher_details_bus(numb){ 
  struct bus *trouver_bus(int numb) {
   for (int i = 0; i < nb_bus; i++) {
    if (buses[i].numero_bus ==numb) {
      return &buses[i];
    }
   }
   return NULL;
   if (bus == NULL) {
    printf("ce bus n'existe pas !\n");
    return;
   }
}
   printf("** Détails du bus **\n");
   printf("Bus %d - Destination : %s - nombre de places : %d - disponibilité(O/N):%c \n", bus.numero_bus, bus.destination, bus.nbre_places,b.disponibilite);
}
void afficher_modifier_reservation() {
  int numres;
  printf(" le numero de la reservation : ");
  scanf("%d", &numres);
  struct reservation *trouver_reservation(int numres) {
  for (int i = 0; i < nb_reservations; i++) {
    if (reservations[i].numero_reservation ==numres) {
      return &reservations[i];
    }
  }
  return NULL;
  if (reservation == NULL) {
    printf("La réservation n'existe pas !\n");
    return;
  }
  printf("** Détails de la réservation **\n");
  printf(" le numero de la reservation : %d\n", reservation->numero_reservation);
  printf(" le numero du bus : %d\n", reservation->numero_bus);
  printf(" le  voyageur : %s %s %d %s ", reservation->voyageur->nom,reservation->voyageur->prenom,reservation->voyageur->age,reservation->voyageur->email);
  printf("Date de la réservation : %s\n", reservation->date);
  char choix;
  printf("Souhaitez-vous modifier les détails de la réservation (o/n) ? ");
  scanf("%c", &choix);
  if (choix == 'o') {
    int nv_numbus;
    printf("Nouvel numero du bus : ");
    scanf("%d", &nv_numbus);
    char nv_pr;
    char nv_nom,
    int nv_age;
    char nv_email;
    printf("Nouveau voyageur : ");
    scanf("%s", nv_pr);
    scanf("%s", nv_nom);
    scanf("%d", &nv_age);
    scanf("%s", nv_email);
    Voyageur nouveauvoyageur;
    nouveauvoyageur->prenom=nv_pr;
    nouveauvoyageur->nom=nv_nom;
    nouveauvoyageur->age=nv_age;
    nouveauvoyageur->email=nv_email;
    char nvd;
    printf("Nouvelle date de la réservation (jj/mm/aaaa) : ");
    scanf("%s", nvd);
    reservation->numero_bus=nv_numbus;
    reservation-> =nv_numvg;
    reservation->date = nvd;
    printf("** Détails de la réservation mise à jour **\n");
    printf(" numero de reservation: %d\n",reservation->numero_reservation );
    printf(" numero du bus : %d\n", nv_numbus);
    printf(" le voyageur : %s %s %d %s \n",nv_pr,nv_nom,nv_age,nv_email );
    printf("Date de la réservation : %s\n", nvd);
  }
} 
bus creer_Bus() {
    bus nouveauBus;
    printf("Entrez le numéro du bus : ");
    scanf("%d", &nouveauBus.numero_bus);
    printf("Entrez la destination du bus : ");
    scanf("%s", nouveauBus.destination);
    printf("Entrez le nombre de places dans le bus : ");
    scanf("%d", &nouveauBus.nbre_places);
    printf(" Est ce que le bus est disponible (O/N)?  ");
    scanf("%c",nouveauBus.disponibilite);
    return nouveauBus;
    printf(" Le nouveau bus est créé avec succès !\n");
}
void annuler_Reservation(reservation *res, int *nb_reservations, int numeroReservation) {
    int i;
    int position = -1; 
    for (i = 0; i < *nb_reservations; i++) {
        if (res[i].numero_reservation == numeroReservation) {
            position = i;
            break; 
        }
    }
    if (position != -1) {
        for (i = position; i < (*nb_reservations - 1); i++) {
            res[i] = res[i + 1];
        }
        (*nb_reservations)--;
        printf("La réservation %d a été annulée.\n", numeroReservation);
    } else {
        printf("pas de réservation trouvée avec le numéro %d.\n", numeroReservation);
    }
}
void avisVoyageur(AvisVoyageur *avis, int *tailleAvis, int numeroReservation ) {
    int i;
    int position = -1; 
    for (i = 0; i < *tailleAvis; ++i) {
        if (avis[i].numero_reservation == numeroReservation) {
            position = i;
            break; 
        }
    }

    if (position != -1) {
        printf("Laissez votre avis sur le voyage (max 100 caractères) : ");
        scanf(" %s", avis[position].avis);
        printf("Merci pour votre avis!\n");
    } else {
        printf("Aucune réservation trouvée avec le numéro %d.\n", numeroReservation);
    }
}  
int main() {
    int choix ;
    bus buses ;
    AvisVoyageur avis;
    reservation reservations ;
    Voyageur voyageurs;
    int nb_voyageurs =0;
    int nb_bus = 0;
    int nb_reservations = 0;
    FILE *fichier1 = fopen("voyageurs.txt", "w");
    FILE *fichier2 = fopen("reservations.txt", "w");
    FILE *fichier3 = fopen("buses.txt", "w")
    menu();
    printf(" Qu'est ce que vous voulez faire ?");
    scanf("%d",&choix);
    do{
      switch(choix){
        case 1 :
             creer_compte();
             nb_voyageurs++;
             voyageurs[nb_voyageurs] =creer_compte();
             fprintf(fichier1, "%s %s %d %s \n", voyageurs[nb_voyageurs].nom, voyageurs[nb_voyageurs].prenom, voyageurs[nb_voyageurs].age, voyageurs[nb_voyageurs].email) ;
             break;
        case 2 :
             int numres;
             int numbus;
             char date;
             printf(" donner le numero de reservation : ");
             scanf("%d",&numres);
             printf(" donner le numero de bus : ");
             scanf("%d",&numbus);
             printf(" donner la date: ");
             scanf("%s",date); 
             creerReservation(numres,numbus,date);
             nb_reservations++;
             reservations[nb_reservations]=creerReservation(numres,numbus,date);
             fprintf(fichier2, "%d %d %d %s\n", reservations[nb_reservations].numero_reservation, reservations[nb_reservations].numero_bus, reservations[nb_reservations].numero_voyageur, reservations[nb_reservations].date);            
             break;
        case 3 :
             int numb;
             printf(" entrez le numero de bus que vous voulez afficher ses details ");
             scanf("%d",&numb);
             afficher_details_bus(numb);       
             break;        
        case 4:
             afficher_modifier_reservation()
             break;
        case 5:
             creer_Bus();
             nb_bus++;
             buses[nb_bus]=creer_Bus();
             fprintf(fichier3, "%d %s %d %c \n", bus[i].numero_bus, bus[i].destination, bus[i].nbre_places, bus[i].disponibilite);
             break;     
        case 6:
             int numeroReservation;
             printf(" entrez le numero de la réservation que vous voulez annuler ");
             scanf("%d",&numeroReservation);
             annuler_Reservation(*res, *nb_reservations , numeroReservation);
             break;
        case 7 :
             int ta;
             int numres;
             printf("donner la taille de votre avis ");
             scanf ("%d",&ta);
             printf("donner le numero de la réservation a commenter ");
             scanf("%d",&numres);
             avisVoyageur(*avis,ta, numres );
             break;
        case 0 :
             printf("Au revoir !\n");
             break;
        default:
                printf("Choix incorrect . Veuillez réessayer!.\n");
        }
    } while (choix != 0);
    }       
    fclose(fichier1);
    fclose(fichier2);
    fclose(fichier3);
    return 0;
}
