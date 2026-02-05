Le rôle général du **pipe** (`|`) en Linux est de créer une **chaîne de travail**. Il permet de connecter des commandes simples entre elles pour réaliser une tâche complexe.

### Le Principe Fondamental

Le pipe prend ce qui sort d'une commande (le résultat affiché à l'écran) et le donne immédiatement à manger à la commande suivante comme si vous l'aviez tapé au clavier.

**Formule :** `Commande_A | Commande_B`

- **Commande_A** fait son travail et produit un résultat.
    
- **`|`** attrape ce résultat et le transmet.
    
- **Commande_B** reçoit ce résultat et travaille dessus.
    

---

### Exemples Concrets du Quotidien

Voici des exemples que vous utiliserez très souvent en tant qu'ingénieur cybersécurité :

#### 1. Le Filtrage (La plus courante)

Vous voulez lister les fichiers, mais vous ne voulez voir que ceux qui sont des images `.jpg`.

- **Sans pipe :** `ls` affiche tout (500 fichiers). Vous devez chercher avec vos yeux.
    
- **Avec pipe :**
    
    Bash
    
    ```
    ls -la | grep ".jpg"
    ```
    
    - `ls -la` : Liste tout.
        
    - `grep ".jpg"` : Ne garde que les lignes contenant ".jpg".
        

#### 2. La Pagination (Lire des fichiers géants)

Vous voulez lire un fichier de 10 000 lignes (comme un dictionnaire de mots de passe `rockyou.txt`).

- **Sans pipe :** `cat rockyou.txt` fait défiler tout l'écran en 2 secondes et s'arrête à la fin. Illisible.
    
- **Avec pipe :**
    
    Bash
    
    ```
    cat rockyou.txt | less
    ```
    
    - `cat` : Ouvre le fichier.
        
    - `less` : Prend le contenu et vous permet de naviguer avec les flèches page par page.
        

#### 3. Le Comptage

Vous voulez savoir combien de fichiers il y a dans un dossier.

- **Avec pipe :**
    
    Bash
    
    ```
    ls | wc -l
    ```
    
    - `ls` : Liste les fichiers (1 fichier par ligne).
        
    - `wc -l` : Compte le nombre de lignes qu'il reçoit. (Résultat : `42` par exemple).
        

#### 4. La Recherche dans l'Historique

Vous avez tapé une commande compliquée hier mais vous l'avez oubliée.

- **Avec pipe :**
    
    Bash
    
    ```
    history | grep "ssh"
    ```
    
    - `history` : Affiche vos 1000 dernières commandes.
        
    - `grep "ssh"` : Affiche uniquement les fois où vous avez utilisé SSH.
        

C'est la philosophie de Linux : créer de petits outils qui font **une seule chose** très bien (lister, chercher, compter) et vous laisser les assembler comme des LEGO grâce au pipe.