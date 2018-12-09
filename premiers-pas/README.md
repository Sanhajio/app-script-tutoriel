PIs/GScript/HTTP/Admin SDK
===========================

#HTTP
Protocol de communication WEB qui permet d'effectuer des requêtes vers des serveur distants comme un serveur Apache.
Il existe différents Types de requêtes dont les plus utilisées:
- GET : Pour accéder à google.com, le navigateur effectue une requête HTTP GET, Pour avoir le contenu 
- POST: utilisée pour transmettre des données. utilisée pour transmettre des formulaire par example.
- PUT: Cette méthode permet de remplacer ou d'ajouter une ressource sur le serveur. Moins utilisée que le POST
- DELETE: Cette méthode permet de supprimer une ressource du serveur.

Suite à une requête HTTP, le serveur renvoie une réponse et un code entre 100 et 500, les code les plus courants sont:
200 : succès de la requête ;
401 : utilisateur non authentifié ;
403 : accès refusé ;
404 : page non trouvée ;

URL: http://www.wikipedia.org/ ou https://developers.google.com/admin-sdk/directory/v1/reference/ sont des URL qui accèdent à des resources différentes sur internet.

#APIS
un ensemble normalisé de méthodes ou de fonctions qui sert de façade par laquelle un logiciel offre des services à d'autres logiciels.
API REST est un style d'architecture logicielle définissant un ensemble de contraintes à utiliser pour créer des services web. (D'où la similarité entre les apis web)

Une RESOURCE dans les APIs Restful est une liste de paramètres (clé, valeur) associée à la requête HTTP.
Les ressources web sont souvent décrites en JSON, un format de données textuelles. 

Exemple de format JSON: 
'''Javascript
{
  "roleId": long,
  "rolePrivileges": [
    {
      "privilegeName": string,
      "serviceId": string
    }
  ],
}
'''

Exemple de description d'API Web accessible au dessus du protocol HTTP: https://developers.google.com/admin-sdk/directory/v1/reference/groups

#GScript
Un language de programmation qui donne un accès simple aux ressources/API de Gsuite comme docs, gmail, adminSDK.
Le language est une surcouche de Javascript, il contient les librairies standards de javascript.

Liens:
https://developers.google.com/admin-sdk/directory/
https://developers.google.com/apps-script/advanced/admin-sdk-directory
https://developers.google.com/apps-script/reference/
