
Pour toutes les spécificités d'implémentation Acadia auxquelles j'ai été "mêlé", je me suis concentré sur l'accès à l'objet Account,
et _espéré que les cascades par défaut sur les objets dépendants soient pertinentes_.

>Par ailleurs, vous trouverez ci-dessous un certain nombre de réserve, y compris concernant mes propres choix, avec l'intitulé "_(Question à GUIMINI [...]"_.


# Public Group "Visibilité_large"
C'est mon bricolage le plus voyant : pour modéliser le concept "les gens qui peuvent voir tous les comptes",
j'ai mis en place une _échappatoire_ qui respecte les nouvelles règles mises en place par GUIMINI en Q1 2026.

Ses membres sont affectés de façon variée :
- indirecte, par appartenance à un autre groupe, comme "Team KILI"
- par rôle : "ADV", "Service IT"
- individuellement : "Franck T.", "Alexis I."

Cette fonctionnalité est servie par la Sharing Rule sur Account (en Read only) :

`Shared with = "Group: Visibilité_large"`


> _(Question à GUIMINI : supprimer les affectations "par rôle" et remplacer par une affectation individuelle directe, pour une meilleure homogénéité ?...)_
> _(Question à GUIMINI n°2, plus générale : à l'inverse, si on répond "non" à la question précédente, peut-on réhabiliter les rôles et profils pour affecter des gens aux Groupes ?
> Par exemple, affecter le rôle "Team KILI" au groupe du même nom. Mais de toute façon, c'est vrai que l'équivalent n'est pas possible pour les Permission Sets... )_



# Pool temporaire "vacances"
J'ai mis un petit système de "pool temporaire", pour gérer les vacances, quand le système de binômes (Commercial 2) ne suffit pas.

C'est basé sur la paire de Public Groups suivant :
- tmp_spoils_absents
- tmp_spoils_repreneurs
	
reliés par la Sharing Rule sur Account (en Read/Write)

`Criteria = "Owner in Group: tmp_spoils_absents"
Shred With = "Group: tmp_spoils_repreneurs"`

>  _(Question à GUIMINI : si je me souviens biens, J. CHAN nous avais demandé de réfléchir un moyen de remplacer
>  l'ancien "Pool ADV" (= les comptes qui n'appartiennent "fonctionnellement" à personne), pour que des commerciaux puissent y piocher.
> Je manque de recul pour savoir si cette demande a un quelconque lien avec ce que j'ai mis en place.)_


# Déblocage ciblé des "Export de rapport",
Bon, là c'est simple, j'ai "claqué en dur" les ID du rôle Marketing et d'un utilisateur juste à côté
de l'ID du profil "Sys. Admin." que vous avez vous-mêmes mis, dans cette Transaction Security Policy qui bloque les export de rapport.

> menu "/ item "Block_Report_Export_SecurityPolicies" (ne pas cliquer sur le nom, mais le "bouton flèche bas" tout à droite, puis menu contextuel "View")
> ajout d'exceptions de blocage dans les conditions :
> role ID = 00E7Q000000Hddt (Marketing)
> User ID = 0057Q000003LhvO (Michael DUBRAY)



