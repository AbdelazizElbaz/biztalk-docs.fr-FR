---
title: "Comment configurer un Port d’envoi SMTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [SMTP adapters], send ports
- send ports, SMTP adapters
- SMTP adapters, send ports
ms.assetid: b2291378-718d-4d1a-9d54-cd34c1b2e000
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f69f61af2803272c34e3f4e8a0ac4dccfb151561
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-an-smtp-send-port"></a>Comment configurer un Port d’envoi SMTP
Vous pouvez configurer un port d'envoi SMTP par programme ou à l'aide de la console Administration de BizTalk Server.  
  
 **Comment configurer un Port d’envoi SMTP par programme**  
  
 L'adaptateur SMTP stocke ses informations de configuration dans la base de données de gestion BizTalk (également appelée « base de données de configuration »). Elles sont stockées dans un jeu de propriétés XML personnalisé. Lors de l'initialisation et de l'exécution de l'adaptateur SMTP, le serveur transmet la configuration à l'adaptateur comme suit :  
  
-   Pour le Gestionnaire d’envoi SMTP, les informations de configuration sont transmises à l’adaptateur en appelant le **charge** méthode de la **IPersistPropertyBag** interface.  
  
-   Pour les adaptateurs d'envoi SMTP, les informations de configuration sont transmises à l'adaptateur sous la forme d'un jeu de propriétés dans un contexte de message. L'espace de noms SMTP regroupe ces propriétés.  
  
 Le modèle objet de l'Explorateur BizTalk expose l'interface de configuration d'adaptateur ITransportInfo pour les ports d'envoi contenant la propriété de lecture/écriture TransportTypeData. Cette propriété accepte le jeu de propriétés de configuration du port d'envoi SMTP sous la forme d'une chaîne XML composée d'une paire nom/valeur. Notez que pour définir cette propriété dans le modèle d’objet de l’Explorateur BizTalk, il doit être définie sur la propriété Address de le **ITransportInfo** interface.  
  
 Définition de la **TransportTypeData** propriété de la **ITransportInfo** interface n’est pas requise. Si elle n'est pas définie, l'adaptateur SMTP utilise les valeurs par défaut pour le gestionnaire d'envoi SMTP. Les propriétés spécifiques au port d'envoi SMTP sont définies dans le schéma de propriété de l'adaptateur d'envoi SMTP bts_smtp_properties.xsd.  
  
 Si les propriétés qui dupliquent la configuration du gestionnaire d'envoi ne sont pas définies, les propriétés de configuration pour le gestionnaire sont utilisées. Si les propriétés requises ne sont pas définies, les valeurs par défaut sont utilisées. Si les valeurs par défaut ne sont pas définies, le gestionnaire d'envoi SMTP consigne une erreur dans le journal des événements et déplace le message vers l'adaptateur de secours.  
  
 Vous pouvez définir ces propriétés par programme dans un contexte de message. Vous pouvez définir ces propriétés dans une planification d'orchestration BizTalk ou dans un composant de pipeline personnalisé. Les règles suivantes s'appliquent dans le cadre de l'utilisation de ces propriétés :  
  
-   Si la propriété est définie dans une orchestration ou le composant de pipeline personnalisé dans un pipeline de réception, alors :  
  
    -   Si le message est envoyé à un port d'envoi statique, la valeur de la propriété est remplacée par la valeur configurée pour ce port d'envoi.  
  
    -   Si le message est envoyé à un port d'envoi dynamique, la valeur de la propriété n'est pas remplacée.  
  
-   Si la propriété est définie dans un composant de pipeline personnalisé dans un pipeline d'envoi, alors :  
  
    -   La valeur n'est pas remplacée, que le message soit envoyé à un port d'envoi statique ou dynamique.  
  
 Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir dans le modèle objet de l'Explorateur BizTalk pour l'emplacement d'envoi SMTP.  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|**SMTPHost**|xs:string|Serveur SMTP utilisé pour l'envoi des messages.|Longueur maximale : 256|Valeur par défaut : vide.<br /><br /> La valeur par défaut indique que le port d'envoi SMTP utilisera les valeurs de configuration pour le gestionnaire.|  
|**From**|xs:string|L’adresse de messagerie que le port d’envoi SMTP place sur le protocole SMTP **de** en-tête.|Longueur maximale : 256|Valeur par défaut : vide.<br /><br /> La valeur par défaut indique que le port d'envoi SMTP utilisera les valeurs de configuration pour le gestionnaire.|  
|**CC**|xs:string|Adresse de messagerie vers laquelle une copie du message sera envoyée.|Longueur maximale : 1024|Valeur par défaut : vide<br /><br /> Vous pouvez répertorier différentes adresses de messagerie.|  
|**Subject**|xs:string|En-tête objet pour les messages.|Longueur minimale : 0<br /><br /> Longueur maximale : 256|Valeur par défaut : MessageID %.|  
|**SMTPAuthenticate**|xs:int|Type d'authentification à utiliser.|Aucune|Valeurs valides :<br /><br /> -0 - aucune authentification<br />Authentification de base - 1-<br />-2 - compte du processus (NTLM)<br /><br /> La valeur par défaut indique que le port d'envoi SMTP utilisera les valeurs de configuration pour le gestionnaire. Pour appliquer la valeur par défaut, omettez cette propriété du jeu de propriétés lors de la configuration de la propriété TransportTypeData.|  
|**UserName**|xs:string|Nom d'utilisateur utilisé pour l'authentification sur le serveur SMTP.|Longueur minimale : 0<br /><br /> Longueur maximale : 256|Valeur par défaut : vide<br /><br /> Requiert une valeur si **SMTPAuthenticate** est égal à 1 (authentification de base).|  
|**Mot de passe**|xs:string|Mot de passe de l'utilisateur pour l'authentification sur le serveur SMTP.|Longueur minimale : 0<br /><br /> Longueur maximale : 256|Valeur par défaut : vide<br /><br /> Requiert une valeur si **SMTPAuthenticate** est égal à 1 (authentification de base).|  
|**ReadReceipt**|xs:boolean|Demande une confirmation de lecture pour les messages à partir de ce port d'envoi.|Aucune|Valeur par défaut : False|  
|**DeliveryReceipt**|xs:boolean|Demande un accusé de réception pour les messages à partir de ce port d'envoi.|Aucune|Valeur par défaut : False|  
|**EmailBodyText**|xs:string|Indiquer le texte à utiliser pour le corps du message électronique à envoyer.|Longueur maximale : 64 Ko|Valeur par défaut : vide|  
|**EmailBodyTextCharset**|xs:string|Spécifier le jeu de caractères à utiliser pour coder le corps du message électronique envoyé lorsque la **EmailBodyText** option est utilisée. L’adaptateur SMTP convertit le **EmailBodyText** pour le jeu de caractères spécifié par **EmailBodyTextCharset**.|Aucune|Valeur par défaut : aucun. Vous devez définir la valeur de manière explicite, par exemple, sur UTF-8.<br /><br /> Si aucune valeur n'est définie, le message d'erreur indiqué à la fin de cette rubrique peut s'afficher.|  
|**EmailBodyFile**|xs:string|Indique que le corps du message électronique à envoyer correspond au contenu d'un fichier, et précise le chemin d'accès à ce dernier. Ce chemin d’accès doit être accessible à l’hôte de l’adaptateur SMTP au moment de l’exécution.|Longueur maximale : 256 caractères|Valeur par défaut : vide|  
|**EmailBodyFileCharset**|xs:string|Spécifier le jeu de caractères à utiliser pour coder le corps du message électronique à envoyer si la **EmailBodyFile** est définie. L'adaptateur SMTP n'effectue aucune conversion du fichier ; celui-ci doit être déjà codé dans ce jeu de caractères. Si le fichier inclut une marque d'ordre de tri, l'adaptateur SMTP la supprime.|Aucune|Valeur par défaut : UTF-8 (65001)|  
|**Pièces jointes**|xs:string|Indique qu'un ou plusieurs fichiers sont joints au message électronique, et précise leur chemin d'accès. L'hôte de l'adaptateur SMTP doit pouvoir y accéder au moment de l'exécution.|Longueur maximale : 256 caractères|Valeur par défaut : vide|  
|**MessagePartsAttachments**|xs:int|Indique la méthode utilisée pour joindre les parties d'un message BizTalk à un message électronique|Aucune|Valeurs valides :<br /><br /> Parties de message - 0 - non BizTalk seront utilisés en tant que pièces jointes.<br />-1 - le corps du message BizTalk est envoyé en tant que pièce jointe. Dans ce cas, le **EmailBodyFile** ou **EmailBodyText** propriétés doivent être spécifiées. Si aucune de ces propriétés n'est spécifiée, le corps du message BizTalk est envoyé en tant que corps du message électronique, et non comme pièce jointe.<br />-2 - toutes les parties sont envoyés comme pièces jointes. Toutefois, si **EmailBodyText** ou **EmailBodyFile** ne sont pas spécifiés, puis le corps du message BizTalk est envoyé en tant que corps du message électronique et d’autres parties sont envoyés comme pièces jointes.<br /><br /> Valeur par défaut : 0|  
|**ReplyBy**|xs:dateTime|Remplit le **par réponse** champ d’en-tête dans le message sortant avec la valeur spécifiée.|Cette propriété ne peut pas être définie dans la page de propriété du port d'envoi. Cette propriété peut être définie à partir d'un pipeline ou d'une orchestration.|Valeur par défaut : vide|  
  
 Le code suivant illustre le format de la chaîne XML que vous devez utiliser pour définir ces propriétés :  
  
```  
<CustomProps>  
   <DeliveryReceipt vt="11">-1</DeliveryReceipt  
   <SMTPHost vt="8">sfdsadf</SMTPHost>  
   <Subject vt="8">Some subject</Subject>  
   <From vt="8">username@domain.com</From>  
   <SMTPAuthenticate vt="19">2</SMTPAuthenticate>  
   <ReadReceipt vt="11">-1</ReadReceipt>  
</CustomProps>  
```  
  
 **Comment configurer un Port d’envoi SMTP avec la Console Administration de BizTalk Server**  
  
 Vous pouvez définir les variables de l'adaptateur du port d'envoi SMTP dans la console Administration de BizTalk. Si les propriétés ne sont pas définies pour le port d'envoi, les valeurs par défaut du gestionnaire d'envoi définies dans la console Administration de BizTalk Server sont utilisées.  
  
 La procédure suivante permet de configurer le port d'envoi SMTP à l'aide de la console Administration de BizTalk Server.  
  
### <a name="to-configure-variables-for-an-smtp-send-port"></a>Pour configurer les variables pour un port d'envoi SMTP  
  
1.  Dans la console Administration de BizTalk Server, créez un port d'envoi ou double-cliquez sur un port d'envoi existant pour le modifier. Pour plus d’informations, consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md). Configurez toutes les options de port d’envoi et spécifiez **SMTP** pour le **Type** option dans le **Transport** section de la **général** onglet.  
  
2.  Sur le **général** sous l’onglet le **Transport** section regard **Type**, cliquez sur **configurer**.  
  
3.  Dans le **propriétés du Transport SMTP** boîte de dialogue le **général** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Pour**|Obligatoire. Indiquer l'adresse électronique à laquelle envoyer les messages.<br /><br /> Vous pouvez entrer plusieurs adresses.<br /><br /> Longueur maximale : 256<br /><br /> Pour plus d’informations sur cette propriété, consultez [Restrictions sur la propriété To SMTP](../core/restrictions-on-the-smtp-to-property.md).|  
    |**CC**|Indiquer l'adresse électronique à laquelle envoyer une copie carbone du message.<br /><br /> Vous pouvez entrer plusieurs adresses.<br /><br /> Longueur maximale : 1024|  
    |**Subject**|Indiquer l'en-tête objet du message.<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 256|  
    |**Notification**|Préciser le type d'accusé de notification. Vous pouvez sélectionner l'un ou les deux types d'accusés. Les types d'accusés de notification sont :<br /><br /> -   **Confirmation de lecture**. un message de confirmation est envoyé dès que le message est lu.<br />-   **Accusé de réception**. Message électronique de confirmation est envoyé lorsque le message est remis.|  
  
4.  Dans le **propriétés du Transport SMTP** boîte de dialogue le **composition** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Corps du message BizTalk**|Indiquer qu'il faut utiliser le corps du message BizTalk pour le corps du message électronique à envoyer.|  
    |**Texte**|Indiquer le texte à utiliser pour le corps du message électronique à envoyer. Après le **texte** option est sélectionnée. vous pouvez entrer le texte du corps du message dans la zone de texte.<br /><br /> **Longueur maximale :** 64 Ko|  
    |**Jeu de caractères du texte**|-Spécifiez le jeu de caractères à utiliser pour coder le corps du message électronique envoyé. Cette option est disponible uniquement si le **texte** option est sélectionnée.<br />-   **Valeur par défaut :** UTF-8 (65001)|  
    |**Fichier**|Indiquer que le corps du message électronique à envoyer sera le contenu d'un fichier, et préciser le chemin d'accès à ce dernier. Après le **fichier** option est sélectionnée. vous pouvez cliquer sur le bouton de sélection (**...** ) bouton pour accéder au fichier.<br /><br /> Longueur maximale : 256 caractères **Remarque :** il est recommandé de spécifier un chemin d’accès sur un partage de fichiers qui est accessible à partir de tous les serveurs BizTalk du groupe BizTalk Server à utiliser en production.|  
    |**Jeu de caractères du fichier**|Indiquer le jeu de caractères de codage du fichier envoyé. **Remarque :** l’adaptateur SMTP n’applique pas l’encodage spécifié dans le fichier. Cette option sert uniquement à spécifier que le fichier en cours d'envoi est déjà codé. <br /><br /> Cette option est disponible uniquement si le **fichier** option est sélectionnée.<br /><br /> Valeur par défaut : UTF-8 (65001)|  
  
5.  Dans le **propriétés du Transport SMTP** boîte de dialogue le **des pièces jointes** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Parties de message BizTalk restants**|Indiquer la méthode utilisée pour joindre les parties de message BizTalk à un message électronique.<br /><br /> Options :<br /><br /> -   **Ne pas joindre les parties**<br />-   **Joindre que le corps**<br />-   **Joindre toutes les parties**<br /><br /> Valeur par défaut : ne pas joindre les parties.|  
    |**Ajouter**|Indiquer un ou plusieurs fichiers à joindre à un courrier électronique. Après avoir cliqué sur **ajouter** vous pouvez parcourir pour sélectionner un fichier et l’ajouter à la liste des fichiers à joindre.<br /><br /> Longueur maximale : 256 caractères **Remarque :** il est recommandé de spécifier un chemin d’accès sur un partage de fichiers qui est accessible à partir de tous les serveurs BizTalk du groupe BizTalk Server à utiliser en production.|  
    |**Supprimer**|Supprimer le fichier sélectionné de la liste des fichiers à joindre à un message électronique.|  
  
6.  Dans le **propriétés du Transport SMTP** boîte de dialogue le **remplacement du gestionnaire** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom du serveur SMTP**|Indiquer le nom du serveur SMTP à utiliser pour l'envoi des messages.<br /><br /> Longueur maximale : 256 **Remarque :** URI pour un envoi de port ou de réception emplacement ne peut pas dépasser 256 caractères.|  
    |**À partir de (adresse de messagerie)**|Spécifiez l’adresse de messagerie à placer sur le protocole SMTP **de** en-tête.<br /><br /> Longueur maximale : 256|  
    |**Type d'authentification**|Indique le type d'authentification à utiliser avec le serveur SMTP.<br /><br /> Options :<br /><br /> -   **(Par défaut)**<br />-   **Aucune authentification**<br />-   **Authentification de base**<br />-   **Compte du processus (NTLM)**<br /><br /> La valeur par défaut indique que le port d’envoi SMTP utilisera les valeurs de configuration spécifiés dans le Gestionnaire d’envoi.|  
    |**Nom d'utilisateur**|Indiquer le nom d'utilisateur nécessaire à l'authentification sur le serveur SMTP.<br /><br /> Cette propriété exige une valeur si **type d’authentification** est **l’authentification de base**.<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 256|  
    |**Mot de passe**|Indiquer le mot de passe nécessaire à l'authentification sur le serveur SMTP.<br /><br /> Cette propriété exige une valeur si **type d’authentification** est **l’authentification de base**.<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 256|  
  
7.  Cliquez sur **OK** et **OK** pour enregistrer les paramètres.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur SMTP](../core/configuring-the-smtp-adapter.md)