---
title: "Stockage des données pour les Messages EDI sortants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6e576fc-37fd-417d-ae68-607a0a8bcc0a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f98d5113c63e29f3f4b85834b7ca1aa0836d0a5d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-data-is-stored-for-outbound-edi-messages"></a>Stockage des données pour les messages EDI sortants
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] effectue les opérations suivantes pour générer une entrée de rapport d'état pour un échange sortant :  
  
1.  Lorsqu'un message XML sortant est envoyé au pipeline d'envoi EDI, le pipeline d'envoi crée une entrée dans le magasin de données des rapports d'état, avec les valeurs suivantes :  
  
    -   L'entrée d'état de l'échange est définie sur Traité  
  
    -   L'entrée d'état de l'accusé de réception de l'échange (une par échange) est définie sur Attendu  
  
    -   Les entrées d'état d'accusé de réception fonctionnel (un par groupe dans X12 et un pour tous les groupes dans EDIFACT) sont définies sur Généré.  
  
2.  Une fois le message EDI envoyé au partenaire commercial et l'accusé de réception renvoyé par le partenaire commercial, le pipeline de réception EDI qui reçoit l'accusé de réception met à jour les entrées d'état de l'échange, d'état de l'accusé de réception de l'échange et d'état de l'accusé de réception fonctionnel vers Accepté/Partiellement accepté/Refusé, selon le cas.  
  
## <a name="data-stored-by-the-send-pipeline-for-outbound-interchanges"></a>Données stockées par le pipeline d'envoi pour les échanges sortants  
 Le pipeline d'envoi crée un enregistrement dans le magasin de données des rapports d'état pour chaque échange qu'il envoie. La plupart des données requises pour l'entrée sont disponibles dans les segments de code de fin et d'en-tête de l'échange (ISA/IEA ou UNB/UNZ). Les autres données sont disponibles dans les propriétés du port d'envoi. Les données stockées sont les suivantes :  
  
-   Type d'enregistrement = état de l'échange  
  
-   Direction de l'échange = Données de mise à jour = Envoyer  
  
-   Récepteur de l'échange = données mises à jour  
  
-   Expéditeur de l'échange = données mises à jour  
  
-   Date de l'échange = données mises à jour  
  
-   Heure de l'échange = données mises à jour  
  
-   ID de contrôle de l'échange = données mises à jour  
  
-   État de l'échange : Traité/Envoyé L'état Traité indique que le pipeline d'envoi a traité et passé l'échange à l'adaptateur d'envoi pour la remise.  
  
-   Nombre de contrôles de l'échange (Groupes/Messages dans X12 respectivement) = Données  
  
-   ID du port d'envoi de l'échange = Données  
  
## <a name="data-stored-by-the-receive-pipeline-for-each-technical-acknowledgment-received-in-response-to-an-outbound-interchange"></a>Données stockées par le pipeline de réception pour chaque accusé de réception technique reçu en réponse à un échange sortant  
 Le pipeline de réception crée un enregistrement dans le magasin de données des rapports d'état pour chaque accusé de réception technique qu'il reçoit. Le pipeline de réception crée un enregistrement de chaque échange reçu dans le magasin de données de rapport de statut. Crée une entrée de rapport d’état d’accusé de réception technique dans le magasin de données pour chaque accusé de réception technique reçu en réponse à un échange envoyé à un partenaire commercial. L'accusé de réception technique est TA1 pour X12 et le message CONTRL, avec uniquement le segment UCI pour EDIFACT. Les données stockées sont les suivantes :  
  
-   Type d'enregistrement = état de l'échange/de l'accusé de réception  
  
-   Direction de l'accusé de réception de l'échange = Envoyer - Données de mise à jour  
  
-   Récepteur de l'échange = données mises à jour (requises à des fins de corrélation)  
  
-   Expéditeur de l'échange = données mises à jour (requises à des fins de corrélation)  
  
-   Date de l'échange = Données de mise à jour (requises pour la corrélation X12)  
  
-   ID de contrôle de l'échange = données mises à jour (requises à des fins de corrélation)  
  
-   État de l’accusé de réception de l’échange = généré ou non Applicable \<Note de référence 0\> -mettre à jour des données  
  
-   ID de contrôle de l'accusé de réception de l'échange = Non évalué - sera appliqué par le côté envoi  
  
-   Date de l'accusé de réception de l'échange = Non évalué - sera appliqué par le côté envoi  
  
-   Heure de l'accusé de réception de l'échange = Non évalué - sera appliqué par le côté envoi  
  
-   L’accusé de réception/Code d’Action = données mises à jour \<note de référence 1\> (à partir de X12-TA104 ou EDIFACT-UCI4) *  
  
-   Code de Note de l’accusé de réception = données mises à jour \<Note de référence 2\> (à partir de X12-TA105, non applicable pour EDIFACT) *  
  
 Les accusés de réception/codes d'action suivants sont utilisés :  
  
|Données dans l'accusé de réception/le code d'action|Description de l’erreur pour les rapports|Commentaire (applicabilité)|  
|------------------------------|-------------------------------------|-------------------------------|  
|Un|Accepté|X12|  
|E|Accepté, erreurs signalées|X12|  
|P|Partiellement accepté|X12|  
|R|Rejeté|X12|  
|4|Rejeté|EDIFACT|  
|8|Accepté/Partiellement accepté|EDIFACT|  
  
 Les codes de note d'accusé de réception suivants sont utilisés :  
  
|Données dans le code de note d'accusé de réception (dans X12)| Description|  
|--------------------------------------|-----------------|  
|000|Réussi|  
|001|Numéro de contrôle de l'échange incompatible|  
|002|Norme non prise en charge|  
|003|Version des contrôles non pris en charge.|  
|004|Le terminateur de segment n'est pas valide|  
|005|Le qualificateur d'ID de l'échange n'est pas valide pour l'expéditeur|  
|006|ID de l'expéditeur de l'échange non valide|  
|007|Le qualificateur d'ID de l'échange n'est pas valide pour le destinataire|  
|008|ID du récepteur de l'échange non valide|  
|009|ID du récepteur de l'échange inconnu|  
|010|Valeur du qualificateur d’informations d’autorisation non valide|  
|011|Valeur des informations d’autorisation non valide|  
|012|Valeur du qualificateur d’informations de sécurité non valide|  
|013|Valeur des informations de sécurité non valide|  
|014|Valeur de Date d’échange non valide|  
|015|Valeur d’heure échange non valide|  
|016|Valeur d’identificateur de normes échange non valide|  
|017|Valeur de l'ID de version de l'échange non valide|  
|018|Valeur de numéro de contrôle échange non valide|  
|019|Valeur de l'accusé de réception demandé non valide|  
|020|Valeur de l'indicateur de test non valide|  
|021|Valeur du nombre de groupes inclus non valide|  
|022|Structure de contrôle non valide|  
|023|Fin de fichier incorrecte|  
|024|Contenu de l'échange non valide|  
|025|Numéro de contrôle de l'échange dupliqué|  
|026|Séparateur d'éléments de données non valide|  
|027|Séparateur d'éléments composites non valide|  
|028|Date de remise non valide dans la demande de remise différée|  
|029|Heure de remise non valide dans la demande de remise différée|  
|030|Temps de remise non valide dans la demande de remise différée|  
|031|Catégorie de service non valide|  
  
## <a name="data-updated-by-the-receive-pipeline-for-each-technical-acknowledgment-received-in-response-to-an-outbound-interchange"></a>Données mises à jour par le pipeline de réception pour chaque accusé de réception technique reçu en réponse à un échange sortant  
 Le pipeline de réception met à jour l'entrée du rapport d'état corrélée à l'échange envoyé pour chaque accusé de réception technique qu'il reçoit.  
  
 Le Désassembleur EDI localise les enregistrements dans le magasin de données à l'aide des données contenues dans les segments UCI et TA1 de l'accusé de réception entrant, en procédant comme suit :  
  
|Champs de l'accusé de réception|Champs du magasin de données|Commentaire|  
|-------------------|--------------------------|-------------|  
|ID de l'expéditeur de l'échange|Récepteur de l'échange|-|  
|ID du récepteur de l'échange|Expéditeur de l'échange|-|  
|-|Date de l'échange|-|  
|Numéro de contrôle d’échange|ID de contrôle de l'échange|-|  
|-|Direction de l'échange = Envoyer|Requis pour assurer l'unicité des lots conservés|  
|Type d'enregistrement|État de l'échange et état de l'accusé de réception de l'échange|-|  
  
 Les données stockées sont les suivantes :  
  
-   Direction de l'accusé de réception de l'échange = Recevoir - Données existantes  
  
-   État de l'accusé de réception de l'échange = Reçu  
  
-   Récepteur de l'échange = données existantes  
  
-   Expéditeur de l'échange = données existantes  
  
-   Date de l'échange = données existantes  
  
-   ID de contrôle de l'échange = données existantes  
  
-   ID de contrôle de l'accusé de réception de l'échange = données mises à jour  
  
-   Date de l'accusé de réception de l'échange = données mises à jour  
  
-   Heure de l'accusé de réception de l'échange = données mises à jour  
  
-   L’accusé de réception/Code d’Action = données mises à jour (à partir de X12-TA104 ou EDIFACT-UCI4) * \<Note de référence 1\>  
  
-   Code de Note de l’accusé de réception 2 = données mises à jour (à partir de X12-TA105, non évalué pour EDIFACT) * \<Note de référence 2\>  
  
 Les données de ACK X12:TA1-104 ou EDIFACT UCI4 doivent être mappées comme suit :  
  
|Données dans l'accusé de réception/le code d'action|Mappage pour les rapports d'état|Commentaire|  
|------------------------------|---------------------------------|-------------|  
|Un|Accepté|X12|  
|P|Partiellement accepté|X12|  
|R, M, W, X|Rejeté|X12|  
|E|Accepté avec des erreurs|X12|  
|4|Rejeté|EDIFACT|  
|7, 8|Accepté/Partiellement accepté|EDIFACT|  
  
 Les codes de note d'accusé de réception suivants sont utilisés :  
  
|Données dans le code de note d'accusé de réception (dans X12)|Mappage pour les rapports d'état|  
|--------------------------------------|---------------------------------|  
|000|Réussi|  
|001|Numéro de contrôle de l'échange incompatible|  
|002|Norme non prise en charge|  
|003|Version des contrôles non pris en charge.|  
|004|Le terminateur de segment n'est pas valide|  
|005|Le qualificateur d'ID de l'échange n'est pas valide pour l'expéditeur|  
|006|ID de l'expéditeur de l'échange non valide|  
|007|Le qualificateur d'ID de l'échange n'est pas valide pour le destinataire|  
|008|ID du récepteur de l'échange non valide|  
|009|ID du récepteur de l'échange inconnu|  
|010|Valeur du qualificateur d’informations d’autorisation non valide|  
|011|Valeur des informations d’autorisation non valide|  
|012|Valeur du qualificateur d’informations de sécurité non valide|  
|013|Valeur des informations de sécurité non valide|  
|014|Valeur de Date d’échange non valide|  
|015|Valeur d’heure échange non valide|  
|016|Valeur d’identificateur de normes échange non valide|  
|017|Valeur de l'ID de version de l'échange non valide|  
|018|Valeur de numéro de contrôle échange non valide|  
|019|Valeur de l'accusé de réception demandé non valide|  
|020|Valeur de l'indicateur de test non valide|  
|021|Valeur du nombre de groupes inclus non valide|  
|022|Structure de contrôle non valide|  
|023|Fin de fichier incorrecte|  
|024|Contenu de l'échange non valide|  
|025|Numéro de contrôle de l'échange dupliqué|  
|026|Séparateur d'éléments de données non valide|  
|027|Séparateur d'éléments composites non valide|  
|028|Date de remise non valide dans la demande de remise différée|  
|029|Heure de remise non valide dans la demande de remise différée|  
|030|Temps de remise non valide dans la demande de remise différée|  
|031|Catégorie de service non valide|  
  
## <a name="data-stored-by-the-receive-pipeline-for-each-functional-acknowledgment-received-in-response-to-outbound-interchanges"></a>Données stockées par le pipeline de réception pour chaque accusé de réception fonctionnel reçu en réponse à des échanges sortants  
 Le pipeline de réception crée un enregistrement dans le magasin de données des rapports d'état pour chaque accusé de réception fonctionnel qu'il reçoit.  L'accusé de réception technique est 997 pour X12 et le message CONTRL complet pour EDIFACT. Une entrée par groupe est créée. Les données des en-têtes d'échange et de groupe sont utilisées lors de la création de cette entrée. Les données stockées sont les suivantes :  
  
-   Type d'enregistrement = état de l'accusé de réception fonctionnel  
  
-   Direction de l'accusé de réception fonctionnel = Envoyer  
  
-   État de l’accusé de réception fonctionnel = \<généré ou non Applicable, note de référence 1\>  
  
-   Récepteur de l'échange = données mises à jour (requises à des fins de corrélation)  
  
-   Expéditeur de l'échange = données mises à jour (requises à des fins de corrélation)  
  
-   Date de l'échange = Données de mise à jour (requises pour la corrélation X12)  
  
-   ID de contrôle de l'échange = données mises à jour (requises à des fins de corrélation)  
  
-   Numéro de contrôle du groupe = Données de mise à jour (facultatives pour EDIFACT et requises pour la corrélation X12)  
  
-   Code de l'ID fonctionnel = Données de mise à jour (GS01/UNG01)  
  
-   Nombre de documents informatisés = Données de mise à jour (UNE1/UNZ1)  
  
-   ID de contrôle de l'échange d'accusé de réception fonctionnel = Non évalué - sera appliqué par le côté envoi  
  
-   Date de l'échange d'accusé de réception fonctionnel = Non évalué - sera appliqué par le côté envoi  
  
-   Heure de l'échange d'accusé de réception fonctionnel = Non évalué - sera appliqué par le côté envoi  
  
-   Nombre de documents informatisés reçus = Données de mise à jour (X12-AK903 et calculé par le moteur pour le codage EDIFACT)  
  
-   Nombre de documents informatisés acceptés = Données de mise à jour (X12-AK904 et calculé par le moteur pour le moteur EDIFACT)  
  
-   L’accusé de réception/Code d’Action = données mises à jour \<note de référence 2\> (à partir de X12-AK901 ou EDIFACT-UCI4) *  
  
-   Erreur/Code d'erreur de syntaxe = Données de mise à jour (X12-AK905, EDIFACT UCI5) Note 3  
  
-   Code d'erreur 2 supplémentaire de l'accusé de réception X12 = Données de mise à jour (X12-AK906)  
  
-   Code d'erreur 3 supplémentaire de l'accusé de réception X12 = Données de mise à jour (X12-AK907)  
  
-   Code d'erreur 4 supplémentaire de l'accusé de réception X12 = Données de mise à jour (X12-AK908)  
  
-   Code d'erreur 5 supplémentaire de l'accusé de réception X12 = Données de mise à jour (X12-AK909)  
  
 Les Codes de l’accusé de réception/Action suivant sera utilisés :  
  
|Données dans l'accusé de réception/le code d'action|Description de l’erreur pour les rapports|Commentaire (applicabilité)|  
|------------------------------|-------------------------------------|-------------------------------|  
|Un|Accepté|X12|  
|E|Accepté avec des erreurs|X12|  
|P|Partiellement accepté|X12|  
|R|Rejeté|X12|  
|4|Rejeté|EDIFACT|  
|7|Accepté/Partiellement accepté|EDIFACT|  
  
 Les erreurs/codes d'erreur suivants sont utilisés pour EDIFACT :  
  
|Données dans la syntaxe de l’erreur/Code d’erreur<br /><br /> (applicable à EDIFACT)|Description de l'erreur pour les rapports|  
|--------------------------------------------------------------------|-------------------------------------|  
|2|Version ou niveau de la syntaxe non pris en charge|  
|7|Le destinataire de l'échange n'est pas le destinataire réel|  
|12|Valeur non valide|  
|13|Manquant|  
|14|Valeur non prise en charge à cette position|  
|15|Non pris en charge à cette position|  
|16|Trop de composants|  
|17|Aucun accord|  
|18|Erreur inconnue|  
|19|Notation décimale non valide|  
|20|Caractère non valide en tant que caractère de service|  
|21|Caractère(s) non valide(s)|  
|22|Caractère(s) de service non valide(s)|  
|23|Expéditeur de l'échange inconnu|  
|24|Trop ancien|  
|25|L'indicateur Test n'est pas pris en charge|  
|26|Doublon détecté|  
|27|La fonction de sécurité n'est pas prise en charge|  
|28|Les références ne correspondent pas|  
|29|Le nombre de contrôles ne correspond pas au nombre d'instances reçues|  
|30|Groupes et messages/packages mélangés|  
|31|Plusieurs types de messages dans le groupe|  
|32|Niveau inférieur vide|  
|33|Occurrence non valide hors du message, du package ou du groupe|  
|34|Indicateur d'imbrication non autorisé|  
|35|Trop d'éléments de données ou de répétitions de segments|  
|36|Trop de répétitions de groupes de segments|  
|37|Type de caractère non valide|  
|38|Chiffre manquant devant le signe décimal|  
|39|Élément de données trop long|  
|40|Élément de données trop court|  
|41|Erreur permanente du réseau de communication|  
|42|Erreur temporaire du réseau de communication|  
|43|Destinataire de l'échange inconnu|  
|45|Séparateur de fin|  
|46|Jeu de caractères non pris en charge|  
|47|La fonctionnalité d'enveloppe n'est pas prise en charge.|  
|48|Condition de dépendance violée|  
|70|Document informatisé est manquant ou identificateur de document informatisé non valide|  
|71|Document informatisé ou numéro de contrôle du groupe incohérent|  
|72|ID de segment non reconnu|  
|73|XML n'est pas à la position correcte|  
|74|Répétitions de groupes de segments insuffisantes|  
|75|Répétitions de segments insuffisantes|  
|76|Éléments de données trouvés insuffisants|  
  
 Les erreurs/codes d'erreur suivants sont utilisés pour X12 :  
  
|Données dans la syntaxe de l’erreur/Code d’erreur<br /><br /> (applicable à X12)|Description de l'erreur pour les rapports|  
|----------------------------------------------------------------|-------------------------------------|  
|1|Groupe fonctionnel non pris en charge|  
|2|Version de groupe fonctionnel non pris en charge.|  
|3|Code de fin de groupe fonctionnel manquant|  
|4|Le numéro de contrôle de groupe dans l'en-tête et le code de fin du groupe fonctionnel ne correspondent pas|  
|5|Le nombre de documents informatisés inclus ne correspond pas au nombre réel|  
|6-26|Autres erreurs de validation non prises en charge|  
  
## <a name="data-updated-by-the-receive-pipeline-for-each-functional-acknowledgment-received-in-response-to-outgoing-interchanges"></a>Données mises à jour par le pipeline de réception pour chaque accusé de réception fonctionnel reçu en réponse à des échanges sortants  
 Le pipeline de réception met à jour l'entrée du rapport d'état corrélée à l'échange envoyé pour chaque accusé de fonctionnel qu'il reçoit.  
  
 Le désassembleur EDI localise les enregistrements dans le magasin de données à l'aide des données contenues dans les segments échange et en-tête de groupe de l'accusé de réception entrant, en procédant comme suit :  
  
|Champs de l'accusé de réception|Champs du magasin de données|Commentaire|  
|-------------------|--------------------------|-------------|  
|ID de l'expéditeur de l'échange|Récepteur de l'échange|Applicable à X12 et à EDIFACT|  
|ID du récepteur de l'échange|Expéditeur de l'échange|Applicable à X12 et à EDIFACT|  
|-|Date de l'échange|-|  
|Numéro de contrôle d’échange|ID de contrôle de l'échange|Applicable uniquement à EDIFACT|  
|Numéro de contrôle du groupe|Numéro de contrôle du groupe|Applicable uniquement à X12|  
|-|Direction de l'échange = Envoyer|Requis pour assurer l'unicité des messages BIBO|  
|Type d'enregistrement|État de l'accusé de réception fonctionnel|Applicable à X12 et à EDIFACT|  
  
 Les données stockées sont les suivantes :  
  
-   Type d'enregistrement = état de l'accusé de réception fonctionnel  
  
-   Direction de l'accusé de réception fonctionnel = réception  
  
-   État de l'accusé de réception fonctionnel = Données de mise à jour telles que reçues  
  
-   Récepteur de l'échange = données existantes  
  
-   Expéditeur de l'échange = données existantes  
  
-   Date de l'échange = données existantes  
  
-   ID de contrôle de l'échange = données existantes  
  
-   Numéro de contrôle du groupe = données existantes  
  
-   Code de l'ID fonctionnel = données existantes  
  
-   Nombre de documents informatisés = données existantes  
  
-   Accusé de réception fonctionnel pour l'ID de contrôle de l'échange = données mises à jour  
  
-   Accusé de réception fonctionnel pour la date de l'échange = données mises à jour  
  
-   Accusé de réception fonctionnel pour l'heure de l'échange = données mises à jour  
  
-   Nombre de documents informatisés remis = Données de mise à jour (X12-AK903 et non applicable pour EDIFACT)  
  
-   Nombre de documents informatisés acceptés = Données de mise à jour (X12-AK904 et non applicable pour EDIFACT)  
  
-   Accusé de réception/Code d'action = Données de mise à jour (X12 AK901 et UCI4) Note de référence 1  
  
-   Erreur/Code d'erreur de syntaxe = (X12 AK905 et UCI5) Note de référence 2  
  
-   Code d'erreur 2 supplémentaire de l'accusé de réception X12 = Données de mise à jour (X12-AK906)  
  
-   Code d'erreur 3 supplémentaire de l'accusé de réception X12 = Données de mise à jour (X12-AK907)  
  
-   Code d'erreur 4 supplémentaire de l'accusé de réception X12 = Données de mise à jour (X12-AK908)  
  
-   Code d'erreur 5 supplémentaire de l'accusé de réception X12 = Données de mise à jour (X12-AK909)  
  
 Les Codes de l’accusé de réception/Action suivant sera utilisés :  
  
|Données dans l'accusé de réception/le code d'action|Mappage pour les rapports d'état|Commentaire|  
|------------------------------|---------------------------------|-------------|  
|Un|Accepté|X12|  
|P|Partiellement accepté|X12|  
|R, M, W, X|Rejeté|X12|  
|E|Accepté avec des erreurs|X12|  
|4|Rejeté|EDIFACT|  
|7, 8|Accepté/Partiellement accepté|EDIFACT|  
  
 Les erreurs/codes d'erreur suivants sont utilisés pour EDIFACT :  
  
|Données erronées/code d'erreur de syntaxe<br /><br /> (applicable à EDIFACT)|Description de l'erreur pour les rapports|  
|-------------------------------------------------------------------|-------------------------------------|  
|2|Version ou niveau de la syntaxe non pris en charge|  
|7|Le destinataire de l'échange n'est pas le destinataire réel|  
|12|Valeur non valide|  
|13|Manquant|  
|14|Valeur non prise en charge à cette position|  
|15|Non pris en charge à cette position|  
|16|Trop de composants|  
|17|Aucun accord|  
|18|Erreur inconnue|  
|19|Notation décimale non valide|  
|20|Caractère non valide en tant que caractère de service|  
|21|Caractère(s) non valide(s)|  
|22|Caractère(s) de service non valide(s)|  
|23|Expéditeur de l'échange inconnu|  
|24|Trop ancien|  
|25|L'indicateur Test n'est pas pris en charge|  
|26|Doublon détecté|  
|27|La fonction de sécurité n'est pas prise en charge|  
|28|Les références ne correspondent pas|  
|29|Le nombre de contrôles ne correspond pas au nombre d'instances reçues|  
|30|Groupes et messages/packages mélangés|  
|31|Plusieurs types de messages dans le groupe|  
|32|Niveau inférieur vide|  
|33|Occurrence non valide hors du message, du package ou du groupe|  
|34|Indicateur d'imbrication non autorisé|  
|35|Trop d'éléments de données ou de répétitions de segments|  
|36|Trop de répétitions de groupes de segments|  
|37|Type de caractère non valide|  
|38|Chiffre manquant devant le signe décimal|  
|39|Élément de données trop long|  
|40|Élément de données trop court|  
|41|Erreur permanente du réseau de communication|  
|42|Erreur temporaire du réseau de communication|  
|43|Destinataire de l'échange inconnu|  
|45|Séparateur de fin|  
|46|Jeu de caractères non pris en charge|  
|47|La fonctionnalité d'enveloppe n'est pas prise en charge.|  
|48|Condition de dépendance violée|  
|70|Document informatisé est manquant ou identificateur de document informatisé non valide|  
|71|Document informatisé ou numéro de contrôle du groupe incohérent|  
|72|ID de segment non reconnu|  
|73|XML n'est pas à la position correcte|  
|74|Répétitions de groupes de segments insuffisantes|  
|75|Répétitions de segments insuffisantes|  
|76|Éléments de données trouvés insuffisants|  
  
 Les erreurs/codes d'erreur suivants sont utilisés pour X12 :  
  
|Données dans la syntaxe de l’erreur/Code d’erreur<br /><br /> (applicable à X12)|Description de l'erreur pour les rapports|  
|----------------------------------------------------------------|-------------------------------------|  
|1|Groupe fonctionnel non pris en charge|  
|2|Version de groupe fonctionnel non pris en charge.|  
|3|Code de fin de groupe fonctionnel manquant|  
|4|Le numéro de contrôle de groupe dans l'en-tête et le code de fin du groupe fonctionnel ne correspondent pas|  
|5|Le nombre de documents informatisés inclus ne correspond pas au nombre réel|  
|6-26|Autres erreurs de validation non prises en charge|  
  
## <a name="see-also"></a>Voir aussi  
 [Stockage des données pour les rapports d’état AS2 et EDI](../core/how-data-is-stored-for-edi-and-as2-status-reports.md)   
 [Mode de stockage des données pour les messages EDI entrants](../core/how-data-is-stored-for-inbound-edi-messages.md)