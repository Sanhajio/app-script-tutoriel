GScript/Javascript
=================
GScript/Javascript sont des languages de programmtion multi-paradigme, i.e qui permet de tout faire comme le Java, et Orienté Objet.

#Concept Généraux aux languages de programmation
- Instruction: Une action à effectuer, e.g Manipulation de nombres, chaîne de caractères...
- Variable: un identifiant qui contient de l'information; x = 3. x est un identifiant, 3 est une constante.
- Condition: une expression mathématique évalué à vrai ou faux (x == 3) qui permet d'effectuer une instruction if (x==3) then x-3
- Boucle: Une instruction qui permet de répéter une partie du code.
- Type: Classification d'une valeur: nombre, chaîne de caractère, Liste... Bien que implicite en Javascript, les opérations effectué sur une variable/Constante dépend de son type.
- Fonctions: Notions qui permet de regrouper un ensemble d'instruction, opérations dans le but de les réutiliser.
- Module/Classe: Notions qui permettent d'encapsuler un ensemble de fonctions, de variable.

Dans les languages de programmation, chaque concept est déclaré par un ensemble de mot clé, en javascript/Gscript: "var" permet de déclarer une variable. 

#GScript/Admin directory API
Le but étant de lire la documentation officiel de l'API REST présente https://developers.google.com/admin-sdk/directory/v1/reference/ et d'écrire le code gscript correspondant.

Exemple pour gérer les membres d'un groupe:
API Officiel: https://developers.google.com/admin-sdk/directory/v1/reference/members
Information importante: 
- https://developers.google.com/admin-sdk/directory/v1/reference/members#resource-representations
- https://developers.google.com/admin-sdk/directory/v1/reference/members#methods

Lister tous les membres d'un groupe:
https://developers.google.com/admin-sdk/directory/v1/reference/members/list

'''Javascript
/* Dans la Documentation:
HTTP request: GET https://www.googleapis.com/admin/directory/v1/groups/groupKey/members
Parameter name	Value		Description
groupKey	string		Identifies the group in the API request. The value can be the group's email address, group alias, or the unique group ID.
maxResults	integer		Maximum number of results to return. Default is 200.
pageToken	string		Token to specify the next page in the list.
roles		string		The roles query parameter allows you to retrieve group members by role. Allowed values are OWNER, MANAGER, and MEMBER.

Request body
Do not supply a request body with this method.

Response
If successful, this method returns a response body with the following structure:
{
  "kind": "admin#directory#members",
  "etag": etag,
  "members": [
    members Resource
  ],
  "nextPageToken": string
}

*/

/* Le code correspondant */ 
function listAllMembers() {
  var response; // On declare la variable qui contient la repoonse de la requete http
  var groupEmail = "group.email@domain.org" // Comme decrit dans le tableau des parametres
  var groupKey = groupEmail // Objet Json qui décrit la valeur attendu par lurl  HTTP "groupKey"

  response = AdminDirectory.Members.list(groupKey) // On appelle la fonction list de la class AdminDirectory Members, comme dans HTTP request URL. avec le paramètre groupKey.
  Logger.log(response.members) // On navigue dans la reponse comme dans la section response de la documentation. On affiche la réponse dans le journal d'exécution. 
}
'''

Autre exemple pour Members Update:
https://developers.google.com/admin-sdk/directory/v1/reference/members/update

'''Javascript
/* Dans la documentation
Request URL: PUT https://www.googleapis.com/admin/directory/v1/groups/groupKey/members/memberKey
Parameter name	Value	Description
groupKey	string	Identifies the group in the API request. The value can be the group's email address, group alias, or the unique group ID.
memberKey	string	Identifies the group member in the API request. A group member can be a user or another group. The value can be the member's (group or user) primary email address, alias, or unique ID.

Request body
Property name		Value	Description	Notes
delivery_settings	string	Defines mail delivery preferences of member 
role			string	The member's role in a group. The API returns an error for cycles in group memberships. For more information about a member's role, see the administration help center. 

Response
If successful, this method returns a Members resource in the response body.
{
  "kind": "admin#directory#member",
  "etag": etag,
  "id": string,
  "email": string,
  "role": string,
  "type": string,
  "status": string,
  "delivery_settings": string
}
*/

/* Code Correspondant */
function listAllMembers() {
  var response; 
  var groupEmail = "group.email@domain.org" 
  var memberEmail = "member.email@domain.org"
  
  var groupKey = groupEmail // Objet Json qui décrit la valeur attendu par lurl HTTP "groupKey"
  var memberKey = memberEmail // Objet Json qui décrit la valeur attendu par lurl HTTP "memberKey"

  var requestBody = {"delivery_settings": "NONE", "role": "MANAGER"}

  response = AdminDirectory.Members.update(groupKey, memberKey, requestBody) 
  Logger.log(response) 
}

'''
