
from pathlib import Path
import re

# Dossier contenant les fiches Obsidian
DOSSIER = Path("/residanat")

# Fichier final
FICHIER_SORTIE = DOSSIER / "Réflexes stratégiques — Résidanat.md"

# Titres possibles de la section
TITRE_RECHERCHE = re.compile(
    r"
from pathlib import Path
import re

# Dossier contenant les fiches Obsidian
DOSSIER = Path("/residanat")

# Fichier final
FICHIER_SORTIE = DOSSIER / "Réflexes stratégiques — Résidanat.md"

# Titres possibles de la section
TITRE_RECHERCHE = re.compile(
    r"^#{1,6}\s*Réflexe[s]?\s+stratégique[s]?\s*$",
    re.IGNORECASE | re.MULTILINE
)

# Extensions de fichiers à ignorer
FICHIERS_IGNORES = {
    FICHIER_SORTIE.resolve()
}

def extraire_section(contenu):
    """
    Extrait le contenu de la section Réflexe stratégique
    jusqu'au prochain titre de même niveau ou supérieur.
    """
    lignes = contenu.splitlines()
    debut = None
    niveau = None

    # Chercher le titre de la section
    for i, ligne in enumerate(lignes):
        match = re.match(
            r"^(#{1,6})\s*Réflexe[s]?\s+stratégique[s]?\s*$",
            ligne,
            re.IGNORECASE
        )

        if match:
            debut = i + 1
            niveau = len(match.group(1))
            break

    if debut is None:
        return None

    # Chercher le prochain titre de même niveau ou supérieur
    fin = len(lignes)

    for i in range(debut, len(lignes)):
        match = re.match(r"^(#{1,6})\s+", lignes[i])

        if match and len(match.group(1)) <= niveau:
            fin = i
            break

    section = "\n".join(lignes[debut:fin]).strip()

    return section if section else None


def main():
    if not DOSSIER.exists():
        print(f"Erreur : le dossier {DOSSIER} n'existe pas.")
        return

    resultats = []

    # Parcourir tous les fichiers Markdown, y compris les sous-dossiers
    fichiers = sorted(DOSSIER.rglob("*.md"))

    for fichier in fichiers:
        if fichier.resolve() in FICHIERS_IGNORES:
            continue

        try:
            contenu = fichier.read_text(encoding="utf-8")
        except UnicodeDecodeError:
            print(f"Fichier ignoré (encodage incompatible) : {fichier}")
            continue

        section = extraire_section(contenu)

        if section:
            # Nom de la fiche sans l'extension .md
            nom_fiche = fichier.stem

            resultats.append(
                f"## {nom_fiche}\n\n{section}"
            )

            print(f"Extrait : {nom_fiche}")

    # Construire le fichier central
    contenu_final = "# Réflexes stratégiques — Résidanat\n\n"

    if resultats:
        contenu_final += "\n\n".join(resultats)
    else:
        contenu_final += "Aucun réflexe stratégique trouvé."

    FICHIER_SORTIE.write_text(contenu_final + "\n", encoding="utf-8")

    print("\nExtraction terminée.")
    print(f"Fiches extraites : {len(resultats)}")
    print(f"Fichier créé : {FICHIER_SORTIE}")


if __name__ == "__main__":
    main()",
    re.IGNORECASE | re.MULTILINE
)

# Extensions de fichiers à ignorer
FICHIERS_IGNORES = {
    FICHIER_SORTIE.resolve()
}

def extraire_section(contenu):
    """
    Extrait le contenu de la section Réflexe stratégique
    jusqu'au prochain titre de même niveau ou supérieur.
    """
    lignes = contenu.splitlines()
    debut = None
    niveau = None

    # Chercher le titre de la section
    for i, ligne in enumerate(lignes):
        match = re.match(
            r"
from pathlib import Path
import re

# Dossier contenant les fiches Obsidian
DOSSIER = Path("/residanat")

# Fichier final
FICHIER_SORTIE = DOSSIER / "Réflexes stratégiques — Résidanat.md"

# Titres possibles de la section
TITRE_RECHERCHE = re.compile(
    r"^#{1,6}\s*Réflexe[s]?\s+stratégique[s]?\s*$",
    re.IGNORECASE | re.MULTILINE
)

# Extensions de fichiers à ignorer
FICHIERS_IGNORES = {
    FICHIER_SORTIE.resolve()
}

def extraire_section(contenu):
    """
    Extrait le contenu de la section Réflexe stratégique
    jusqu'au prochain titre de même niveau ou supérieur.
    """
    lignes = contenu.splitlines()
    debut = None
    niveau = None

    # Chercher le titre de la section
    for i, ligne in enumerate(lignes):
        match = re.match(
            r"^(#{1,6})\s*Réflexe[s]?\s+stratégique[s]?\s*$",
            ligne,
            re.IGNORECASE
        )

        if match:
            debut = i + 1
            niveau = len(match.group(1))
            break

    if debut is None:
        return None

    # Chercher le prochain titre de même niveau ou supérieur
    fin = len(lignes)

    for i in range(debut, len(lignes)):
        match = re.match(r"^(#{1,6})\s+", lignes[i])

        if match and len(match.group(1)) <= niveau:
            fin = i
            break

    section = "\n".join(lignes[debut:fin]).strip()

    return section if section else None


def main():
    if not DOSSIER.exists():
        print(f"Erreur : le dossier {DOSSIER} n'existe pas.")
        return

    resultats = []

    # Parcourir tous les fichiers Markdown, y compris les sous-dossiers
    fichiers = sorted(DOSSIER.rglob("*.md"))

    for fichier in fichiers:
        if fichier.resolve() in FICHIERS_IGNORES:
            continue

        try:
            contenu = fichier.read_text(encoding="utf-8")
        except UnicodeDecodeError:
            print(f"Fichier ignoré (encodage incompatible) : {fichier}")
            continue

        section = extraire_section(contenu)

        if section:
            # Nom de la fiche sans l'extension .md
            nom_fiche = fichier.stem

            resultats.append(
                f"## {nom_fiche}\n\n{section}"
            )

            print(f"Extrait : {nom_fiche}")

    # Construire le fichier central
    contenu_final = "# Réflexes stratégiques — Résidanat\n\n"

    if resultats:
        contenu_final += "\n\n".join(resultats)
    else:
        contenu_final += "Aucun réflexe stratégique trouvé."

    FICHIER_SORTIE.write_text(contenu_final + "\n", encoding="utf-8")

    print("\nExtraction terminée.")
    print(f"Fiches extraites : {len(resultats)}")
    print(f"Fichier créé : {FICHIER_SORTIE}")


if __name__ == "__main__":
    main()",
            ligne,
            re.IGNORECASE
        )

        if match:
            debut = i + 1
            niveau = len(match.group(1))
            break

    if debut is None:
        return None

    # Chercher le prochain titre de même niveau ou supérieur
    fin = len(lignes)

    for i in range(debut, len(lignes)):
        match = re.match(r"^(#{1,6})\s+", lignes[i])

        if match and len(match.group(1)) <= niveau:
            fin = i
            break

    section = "\n".join(lignes[debut:fin]).strip()

    return section if section else None


def main():
    if not DOSSIER.exists():
        print(f"Erreur : le dossier {DOSSIER} n'existe pas.")
        return

    resultats = []

    # Parcourir tous les fichiers Markdown, y compris les sous-dossiers
    fichiers = sorted(DOSSIER.rglob("*.md"))

    for fichier in fichiers:
        if fichier.resolve() in FICHIERS_IGNORES:
            continue

        try:
            contenu = fichier.read_text(encoding="utf-8")
        except UnicodeDecodeError:
            print(f"Fichier ignoré (encodage incompatible) : {fichier}")
            continue

        section = extraire_section(contenu)

        if section:
            # Nom de la fiche sans l'extension .md
            nom_fiche = fichier.stem

            resultats.append(
                f"## {nom_fiche}\n\n{section}"
            )

            print(f"Extrait : {nom_fiche}")

    # Construire le fichier central
    contenu_final = "# Réflexes stratégiques — Résidanat\n\n"

    if resultats:
        contenu_final += "\n\n".join(resultats)
    else:
        contenu_final += "Aucun réflexe stratégique trouvé."

    FICHIER_SORTIE.write_text(contenu_final + "\n", encoding="utf-8")

    print("\nExtraction terminée.")
    print(f"Fiches extraites : {len(resultats)}")
    print(f"Fichier créé : {FICHIER_SORTIE}")


if __name__ == "__main__":
    main()