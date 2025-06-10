################################################################################
# PYTHON - Projet DONJON & DRAGONS
# Classe: 3ttr
# Elève: Hlib (hlib_r)
# TFA 2025
# CEPES Jodoigne
# Token de vérification: IDUKI/SECAD/IDODE
#
# /!\ NE PAS SUPPRIMER LES COMMENTAIRES /!\ sous peine de nullité
#
################################################################################
import math
import random
import sys
import time
from traceback import format_list

######### Initialisations ############################################*GEPIC/ECERE/HUJIH*##########
RED = '\033[91m'
GREEN = '\033[92m'
YELLOW = '\033[93m'
BLUE = '\033[94m'
MAGENTA = '\033[95m'
BOLD = '\033[1m'
RESET = '\033[0m'


def slow_print(text, delay=0.005):
    for char in text:
        print(char, end='', flush=True)
        time.sleep(delay)
    print()


def print_boxed(text):
    width = len(text) + 4
    slow_print(f"{BOLD}{MAGENTA}╔" + "═" * (width - 2) + "╗")
    slow_print("║ " + text + " ║")
    slow_print("╚" + "═" * (width - 2) + "╝" + RESET)


name_p = "<NAME>"
race_p = "<RACE>"
class_p = "<CLASSE>"
xp_p = 0
level_p = 0
hp_p = 0
magItem_p = "Void"
####(features)
for_p = 0
dex_p = 0
con_p = 0
int_p = 0
sag_p = 0
cha_p = 0
####(features/)
####(modifiers)
mod_for_p = 0
mod_dex_p = 0
mod_con_p = 0
mod_int_p = 0
mod_sag_p = 0
mod_cha_p = 0
####(modifiers/)

####(bonus features)
couleurs_yeux = [
    "bleus",
    "verts",
    "marron",
    "noisette",
    "gris",
    "noirs",
    "ambre",
    "violets",
    "rouges"
]
vit_p = 0
init_p = 0
mait_p = 0
poids_p = 0
taille_p = 0
eyes_p = "<EYES>"

imc_p = 0
inter_imc_p = "void"
####(bonus features/)


####(Alignment)
ordre = ["Loyal", "Neutre", "Chaotique"]
morale = ["Bon", "Neutre", "Mal"]
alignment_p = "Void"
####(Alignment/)


########################################################################################
# Etape 1: Pseudo
# Token: IVOFU/DELOM/OKIJI*
########################################################################################

print_boxed("BIENVENUE, AVENTURIER COURAGEUX ")

animaux = ["Cochon", "Dragon", "Elephant", "Géant", "Oiseau", "Serpent", "Singe", "Souris", "Tigre", "Tortue"]
adjectifs = ["Badass", "Enragé", "Froid", "Furieux", "Gentil", "Pompeux", "Rusé", "Sincère", "Sombre", "Triste"]
name_p = input(f"Choisissez un {BLUE}pseudo:{RESET} ")
if name_p != "":
    print("Vous avez choisi", BLUE + name_p + RESET)
else:
    name_p = f"{random.choice(animaux)} {random.choice(adjectifs)}"
    print("J'ai choisi ton pseudo", BLUE + name_p + RESET)

print("-------------------------------")
########################################################################################
# Etape 2: Race
# Token: IMALO/KUHUS/ATOTI*
########################################################################################
races = ["Dragon", "Gnome", "Gobelin", "Half-Dragon", "Half-Ork"]

print_boxed("Choisissez une race:")
i = 1
choice = 0
for race in races:
    print(GREEN, BOLD, i, RESET, race)
    i += 1
while True:
    try:
        choice = int(input("Veuillez entrer votre choix: "))
    except ValueError:
        print(f"{RED}Non non non, il faut choisir un nombre{RESET}")
        continue
    if choice == 1 or choice == 2 or choice == 3 or choice == 4 or choice == 5:
        race_p = races[choice - 1]
        print("Vous avez choisi ", BLUE, races[choice - 1], RESET)
        break
    else:
        print(f"{RED}Ce n'est pas entre 1 et 5{RESET}")
print("-------------------------------")

########################################################################################
# Etape 3: Classe
# Token: EMIBO/KADIH/ICILA*
########################################################################################
classes = ["Archer", "Clerc", "Druide", "Paladin", "Voleur"]
print_boxed("Choisissez une classe :")
i = 1
choice = 0
for classe in classes:
    print(GREEN, i, RESET, classe)
    i += 1
print(GREEN, i, RESET, "Au hazard")
while True:
    try:
        choice = int(input("Veuille entrer ton choix: "))
    except ValueError:
        print(f"{RED}Non non non, il faut choisir un nombre{RESET}")
        continue
    if choice == 1 or choice == 2 or choice == 3 or choice == 4 or choice == 5:
        class_p = classes[choice - 1]
        print("Vous avez choisi ", BLUE, classes[choice - 1], RESET)
        break
    elif choice == 6:
        class_p = random.choice(classes)
        print(f"J'ai choisi la classe {BLUE}{class_p}{RESET} pour vous")
        break
    else:
        print(f"{RED}Ce n'est pas entre 1 et 6{RESET}")

print("-------------------------------")

########################################################################################
# Etape 4: Caractéristiques
# Token: TALIR/AGOVU/RODEK*
########################################################################################
for_p = random.randrange(1, 21)
dex_p = random.randrange(1, 21)
con_p = random.randrange(1, 21)
int_p = random.randrange(1, 21)
sag_p = random.randrange(1, 21)
cha_p = random.randrange(1, 21)

########################################################################################
# Etape 5: Boost
# Token: ELICO/TIKAJ/EFILU*
########################################################################################

# Applique ces boosts pour les races suivantes:
#   • Goblin-Maître -> +3 en Constitution
#   • Kobold -> +2 en Intelligence
#   • Nain -> +2 en Force

# races = [ "Dragon",  "Gnome",  "Gobelin",  "Half-Dragon",  "Half-Ork"]
boost = random.randrange(1, 5)
if (race_p == "Dragon"):
    for_p += boost
    print(f"{BOLD}Dragon{RESET} reçoit un bonus de {YELLOW} {boost} FOR {RESET}")
elif (race_p == "Gnome"):
    dex_p += boost
    print(f"{BOLD} Gnome {RESET} reçoit un bonus de {YELLOW} {boost} DEX {RESET}")
elif (race_p == "Gobelin"):
    con_p += boost
    print(f"{BOLD}Gobelin {RESET} reçoit un bonus de {YELLOW} {boost} CON {RESET}")
elif (race_p == "Half-Dragon"):
    int_p += boost
    print(f"{BOLD}Half-Dragon {RESET} reçoit un bonus de {YELLOW} {boost} INT {RESET}")
elif (race_p == "Half-Ork"):
    sag_p += boost
    print(f"Half-Ork {RESET} reçoit un bonus de {YELLOW}{boost} SAG {RESET}")

vit_p = random.randrange(1, 10)
init_p = random.randrange(1, 10)
mait_p = random.randrange(1, 10)
poids_p = random.randrange(15, 121)
taille_p = random.randrange(50, 251)
eyes_p = random.choice(couleurs_yeux)

print("-------------------------------")

imc_p = round(poids_p / ((taille_p / 100) ** 2), 2)
if imc_p < 18.5:
    inter_imc_p = "sous-poids"
elif 18.5 <= imc_p < 25:
    inter_imc_p = "normal"
elif 25 <= imc_p < 30:
    inter_imc_p = "surpoids"
else:
    inter_imc_p = "Obésité"
print(f"{BOLD}Poids:{RESET} {YELLOW}{poids_p} kg{RESET} ")
print(f"{BOLD}Taille:{RESET} {YELLOW}{taille_p} cm {RESET}")
print(f"{BOLD}IMC:{RESET} {YELLOW} {imc_p} {RESET}")
print(f"{BOLD}Interprétation:{RESET} {YELLOW} {inter_imc_p}{RESET}")

print("-------------------------------")

########################################################################################
# Etape 6: Modificateur
# Token: CIPAB/UGOLA/TALOH*
########################################################################################

mod_for_p = math.floor((for_p - 10) / 2)
mod_dex_p = math.floor((dex_p - 10) / 2)
mod_con_p = math.floor((con_p - 10) / 2)
mod_int_p = math.floor((int_p - 10) / 2)
mod_sag_p = math.floor((sag_p - 10) / 2)
mod_cha_p = math.floor((cha_p - 10) / 2)
print(f"Votre modificateur de {BOLD}la Force {RESET}est {YELLOW}{mod_for_p}{RESET}")
print(f"Votre modificateur de {BOLD}la Dextérité {RESET}est {YELLOW} {mod_dex_p}{RESET}")
print(f"Votre modificateur de {BOLD}la Constitution{RESET} est {YELLOW}{mod_con_p}{RESET}")
print(f"Votre modificateur de {BOLD}L'intelligence {RESET}est {YELLOW}{mod_int_p}{RESET}")
print(f"Votre modificateur de {BOLD}la Sagesse {RESET}est {YELLOW}{mod_sag_p}{RESET}")
print(f"Votre modificateur de {BOLD} la charisme {RESET}est {YELLOW}{mod_cha_p}{RESET}")
print("-------------------------------")

########################################################################################
# Etape 7: XP
# Token: EGEVE/CATAH/OFACO*
########################################################################################
xp_p = random.randrange(0, 3401, 200)
##### Bonus
boost = 0
print(f"{BLUE}Lancés:{RESET}", end=" ")
for i in range(0, 20):
    rand_number = random.randrange(1, 7)
    boost += rand_number
    print(YELLOW, rand_number, RESET, end=" ", flush=True)
    time.sleep(0.2)
boost = boost * 10
xp_p += boost
print("  ")
print(f"=>{BLUE}Bonus XP: {YELLOW}{boost} {RESET}")
print(f"=>{BLUE}XP:{YELLOW} {xp_p} {RESET}")

print("-------------------------------")

########################################################################################
# Etape 8: Niveau
# Token: ENOTA/LODID/APIDU*
########################################################################################
if xp_p < 300:
    level_p = 1
elif xp_p < 900:
    level_p = 2
elif xp_p < 2700:
    level_p = 3
elif xp_p < 6500:
    level_p = 4
elif xp_p >= 6500:
    level_p = 5
print(f"Niveau de ton {BLUE}personnage:{YELLOW} {level_p}{RESET}")

########################################################################################
# Etape 9: Points de vie
# Token: OGIRE/BOVIT/EVEPU*
########################################################################################

hp_p = level_p * 8 + mod_con_p + random.randrange(1, 5)
print(f"Points de {BLUE}vie:{YELLOW} {hp_p}{RESET}")

##### Bonus
boost = 0
print(f"{BLUE}Lancés:{RESET}", end=" ")
for i in range(0, level_p):
    rand_number = random.randrange(0, 5)
    boost += rand_number
    print(YELLOW, rand_number, end=" ", flush=True)
    time.sleep(0.2)

hp_p += boost
print("   ")
print(f"{BLUE}Resultat:{RESET} {boost} -> PV = {YELLOW}{hp_p} {RESET}")

print("-------------------------------")

########################################################################################
# Etape 10: Objet magique
# Token: EJORA/DODAV/ACUPI*
########################################################################################

# classes = [ "Archer",  "Clerc",  "Druide",  "Paladin",  "Voleur"]

if class_p == "Archer":
    magItem_p = "Amulette de Santé"
elif class_p == "Clerc":
    magItem_p = "Écharpe des Vents"
elif class_p == "Druide":
    magItem_p = "Gemme de Détection"
elif class_p == "Paladin":
    magItem_p = "Gilet du Barbare"
elif class_p == "Voleur":
    magItem_p = "Coupelle de Résurrection"
print(f"Ton {class_p} a reçu: {BOLD} {magItem_p}{RESET}")

########################################################################################
# Etape 11: Affichage
# Token: FORIK/EFATU/LOTOT*
########################################################################################
print_boxed("Ton personnage :")
print(f"{BLUE}- Nom: {YELLOW}{name_p}{RESET}")
print(f"{BLUE}- Race: {YELLOW}{race_p}{RESET}")
print(f"{BLUE}- Classe: {YELLOW}{class_p}{RESET}")
print(f"{BLUE}- Points d'XP: {YELLOW}{xp_p}{RESET}")
print(f"{BLUE}- Niveau de ton personnage: {YELLOW}{level_p}{RESET}")
print(f"{BLUE}- Objet Magique: {YELLOW}{magItem_p}{RESET}")

print("                    ")

print_boxed("Caractéristiques:")
print(f"{BLUE}- Force: {YELLOW}{for_p}{RESET}  {BLUE}({YELLOW}{mod_for_p}{BLUE}){RESET}")
print(f"{BLUE}- Dextérité: {YELLOW}{dex_p}{RESET}  {BLUE}({YELLOW}{mod_dex_p}{BLUE}){RESET}")
print(f"{BLUE}- Constitution: {YELLOW}{con_p}{RESET}  {BLUE}({YELLOW}{mod_con_p}{BLUE}){RESET}")
print(f"{BLUE}- Intelligence: {YELLOW}{int_p}{RESET}  {BLUE}({YELLOW}{mod_int_p}{BLUE}){RESET}")
print(f"{BLUE}- Sagesse: {YELLOW}{sag_p}{RESET}  {BLUE}({YELLOW}{mod_sag_p}{BLUE}){RESET}")
print(f"{BLUE}- Charisme: {YELLOW}{cha_p}{RESET}  {BLUE}({YELLOW}{mod_cha_p}{BLUE}){RESET}")
print(f"{BLUE}- Points de vie: {YELLOW}{hp_p}{RESET}")

### Bonus 1
print_boxed("Caractéristiques complémentaires:")
print(f"{BLUE}Votre vitesse: {YELLOW}{vit_p} année lumière{RESET} ")
print(f"{BLUE}Votre initiative: {YELLOW}{init_p} points d'initiativité {RESET} ")
print(f"{BLUE}Votre bonus de maîtrise: {YELLOW}{mait_p} points {RESET} ")
print(f"{BLUE}Couleur de vos yeux: {YELLOW}{eyes_p} {RESET} ")
print(f"{BLUE}Poids: {YELLOW}{poids_p} kg{RESET} ")
print(f"{BLUE}Taille: {YELLOW}{taille_p} cm {RESET}")
print(f"{BLUE}IMC: {YELLOW} {imc_p} {RESET}")
print(f"{BLUE}Interprétation: {YELLOW} {inter_imc_p}{RESET}")
### Bonus 1/


### Bonus 2
if mod_con_p == 0:
    pass
elif mod_con_p > 0:
    print(f"{BLUE}BONUS: {YELLOW}+{mod_con_p}")
else:
    print(f"{BLUE}MALUS: {YELLOW}{mod_con_p}")
### Bonus 2/


########################################################################################
# Etape 12: Alignement
# Token: OMUGE/CUFIS/UMOKO*
########################################################################################

align_ordre = random.choice(ordre)
align_morale = random.choice(morale)

if align_ordre == "Neutre" and align_morale == "Neutre":
    alignment = "Neutre"
else:
    alignment = f"{align_ordre} {align_morale}"

print(f"{BLUE}Alignement: {YELLOW} {alignment} {RESET}")
print("-------------------------------")

print_boxed("C'était un voyage vraiment intéressant, merci pour votre attention")
print_boxed("Bonne chance à vous")


