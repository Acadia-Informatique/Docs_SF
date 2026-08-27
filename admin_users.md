_(note: j'utilise SF en anglais pour simplifier les échanges avec Amit et pour profiter au mieux des aides trouvées sur le web, n'hésitez pas à retraduire)_

# Créer un compte pour un nouvel arrivant :

## Compte utilisateur :

1. On commence par repérer un utilisateur existant "modèle" qu'on va recopier.
      ` => menu "Users" / "Users"`
2. Ensuite on ouvre l'écran de création :
       ` => bouton "New User" `
3. Et on renseigne l'identité :
    - Prénom
    - Nom
    - Email
    - les autres champs obligatoires seront automatiquement remplis : "Alias", "username", "nickname", etc.
4. Puis la configuration :
    - **Role** (modélise la notion de "Business Units" et divise les enregistrements selon la hiérarchie des Rôles. C'est en cours de re-modélisation chez Acadia, donc cela n'a "presque pas" d'effet pour le moment.)
    - **Licence** : ce doit être `Salesforce` (tout court). Si l'option n'est pas présente, c'est qu'il n'y a pas plus de licences disponibles (une par utilisateur **Actif**).
    - **Profile** (= droits de "faire")
5. Enregistrer : `=> bouton "Save"`
  Par défaut, un email est immédiatement envoyé à l'email renseigné et l'utilisateur peut entamer sa démarche d'authentification de façon autonome.
  (De même, il est autonome s'il oublie son mot de passe.)

## Ensemble de permissions :
Les "Permissions sets" visent à remplacer progressivement les profils dans les "best practices" de gestion des droits.
L'intérêt c'est la souplesse : un utilisateur peut cumuler les droits de plusieurs Permissions Sets, indépendamment de son profil.
GUIMINI a mis en place un jeu de Permissions Sets préfixés par "Ps_" ou "PS_", et on n'aura en général qu'un seul à affecter à la fois.

      `=> menu "Users" / "Permission Sets" / item "Ps_XXXX" ou "PS_XXXX" / bouton "Manage Assignments"`


## Groupes Publics :
De la même façon, l'appartenance à des Public Groups va se substituer progressivement à la notion de Rôles.

      `=> menu "Users" / "Public Groups" / ouvrir item "XXX" (pour voir les membres) / bouton "Edit"`

> Nous avons mis en place un **groupe spécial "Visibilité_large"**, qui grâce à une "Règle de partage" dédiée sur l'objet "_Account_" (= Comptes clients),
> permet à tous ses membres de voir tous les comptes. Les ADV et commerciaux "prospecteurs" (Team KILI, commerciaux juniors ou nouveaux arrivants) typiquement
> en feront partie.
> Sinon, l'appartenance au rôle "Direction générale" n'a plus d'effet direct depuis Q1 2026, mais ses membres sont "opportunément" également du profil "System Administrator".


# Quelques exemples récemment appliqués : 

## nouveau Commercial / Marketing / Responsable ADV :
1. Compte utilisateur :
    - Role : respectivement Commercial / Marketing / ADV
    - Profile : Standard Acadia
2. Permissons Set : un seul, respectivement : PS_Commercial / Ps_Marketing / PS_ADV
3. Public Group : aucun, ou optionnellement "Visibilité_large" (ex. Franck T. ou Alexis I.)

## nouveau ADV  :
1. Compte utilisateur :
    - Role : ADV
    - Profile : Standard User
2. Permissons Set : PS_ADV
3. Public Group : aucune assignation directe (le rôle ADV donne accès à "Visibilité_large")


## nouveau membre de la Team KILI
1. Compte utilisateur :
    - Role : Team KILI
    - Profile : Standard Acadia
2. Permission Set : Ps_Team_KILI
3. Public Group : Team KILI (qui donne accès indirectement à "Visibilité_large" )


## nouvel admin IT :
1. Compte utilisateur :
    - Role : Service IT 
    - Profile : System Administator
2. Permission Set : Aucun
3. Public Group : aucune assignation directe (le rôle Service IT donne accès à "Visibilité_large")







      
