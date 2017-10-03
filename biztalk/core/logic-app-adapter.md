---
title: "Adaptateur d’application logique utilisé dans BizTalk Server | Documents Microsoft"
description: "Installer et configurer l’adaptateur Logic Apps pour créer un port de réception, emplacement de réception et port d’envoi dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72f2a5ac-a1f6-4bdb-8c29-8267ede75b17
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faa43c187df7a8eb9fccd2f02f23f16e86b97ce0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="logic-app-adapter"></a>Adaptateur d’application logique

## <a name="overview"></a>Vue d'ensemble
BizTalk Server utilise l’adaptateur Logic Apps pour recevoir des messages à partir d’une application Azure logique, ou envoyer des messages à une application Azure logique. 

Dans Azure, nous créer une application logique. Cette application de la logique du connecteur BizTalk pour se connecter à un emplacement de réception que vous créez sur votre serveur BizTalk Server. Cette rubrique suppose que vous possédez des connaissances avec Azure Logic Apps. Si vous débutez avec les applications de la logique, nous vous suggérons [savoir plus sur les](https://azure.microsoft.com/documentation/articles/app-service-logic-what-are-logic-apps/)et même [créer votre propre logique d’application](https://azure.microsoft.com/documentation/articles/app-service-logic-create-a-logic-app/).

Dans cette rubrique, nous répertorient les étapes permettant de recevoir un message dans BizTalk Server à partir d’une application logique. Autrement dit, l’application logique envoie des messages à un serveur BizTalk Server. Le côté réception utilise des applications dans IIS pour gérer la communication avec le service Azure. Si BizTalk Server est locale, vous également installez une passerelle de données sur le serveur BizTalk et créez une passerelle dans Azure. 

Si BizTalk Server est installé sur une machine virtuelle Azure (VM), vous pouvez choisir d’exposer la machine virtuelle en tant que point de terminaison HTTP (vous obtenez une URL), ou ne pas l’exposer en tant que point de terminaison HTTP. Si vous exposez elle, vous n’avez pas besoin d’utiliser la passerelle. Vous pouvez entrer l’URL dans le connecteur BizTalk dans votre application logique. Si vous n’exposez pas la machine virtuelle (aucune URL), vous devez utiliser la passerelle. Ces étapes sont répertoriées dans cette rubrique.

Nous vous montrent également comment envoyer des messages à partir de BizTalk Server à une application Azure logique. Autrement dit, l’application logique reçoit des messages à partir de BizTalk Server. Le côté envoi est assez simple, comme vous pourrez le constater dans cette rubrique.

Utilisez cette rubrique pour créer un emplacement de réception et un port d’envoi à l’aide de l’adaptateur Logic Apps. Vous pouvez utiliser l’adaptateur LogicApp dans un local (joints à votre domaine) de BizTalk Server ou une machine virtuelle Azure exécutant BizTalk Server. 

## <a name="requirements"></a>Spécifications

- Un abonnement Azure pour vous connecter au portail Azure et créer une application logique.
- Ce paramètre est facultatif. Pour envoyer un message de test à votre application logique, installer un outil de test HTTP, tel que [Fiddler](http://www.telerik.com/fiddler) ou [Postman](https://www.getpostman.com/). Si vous utilisez une autre méthode pour envoyer un message à une application logique, il est inutile d’utiliser ces outils. 

## <a name="receive-messages-from-a-logic-app"></a>Recevoir des messages à partir d’une application de logique

Il existe quelques étapes impliquées pour BizTalk Server recevoir des messages à partir d’une application logique. Cette section décrit ces étapes. Il est possible de que l’interface utilisateur dans Azure change, par conséquent, certaines étapes peut ne pas être exactement comme indiqué. 

#### <a name="prerequisites"></a>Conditions préalables

- Si BizTalk Server est locale, installez et configurez le [passerelle de données locale](https://azure.microsoft.com/documentation/articles/app-service-logic-gateway-install/) pour les applications de la logique. Ensuite, dans Azure, [créer la ressource de passerelle de données](https://azure.microsoft.com/documentation/articles/app-service-logic-gateway-connection/) pour se connecter à votre serveur BizTalk Server.
- Si BizTalk Server est installé sur une machine virtuelle Azure, et la machine virtuelle n’est pas exposée comme un point de terminaison HTTP, puis installez et configurez le [passerelle de données locale](https://azure.microsoft.com/documentation/articles/app-service-logic-gateway-install/) pour les applications de la logique. Ensuite, dans Azure, [créer la ressource de passerelle de données](https://azure.microsoft.com/documentation/articles/app-service-logic-gateway-connection/) pour se connecter à votre serveur BizTalk Server.
- Si BizTalk Server est installé sur une machine virtuelle Azure et que l’ordinateur virtuel est exposé en tant que point de terminaison HTTP, puis la passerelle n'est pas nécessaire ou utilisée. 

### <a name="step-1-install-the-logic-app-adapter"></a>Étape 1 : Installer l’adaptateur de l’application logique

L’adaptateur de l’application logique est un téléchargement distinct et n’est pas inclus dans l’installation de BizTalk Server. 

> [!IMPORTANT] 
> Pour télécharger le LogicAppAdapter.iso :
> 
> 1. Accédez à [l’adaptateur Microsoft BizTalk Server pour les applications de la logique de](https://www.microsoft.com/download/details.aspx?id=54287)et l’enregistrer. 
> 2. Ouvrez le LogicAppAdapter.iso, puis exécutez le **LogicApp Adapter.msi** fichier à installer.

1. Sur votre serveur BizTalk Server, téléchargez et installez l’adaptateur de l’application logique. 

2. Double-sélectionnez **LogicApp Adapter.msi** à installer. Acceptez le contrat de licence, et **installer**.
3. **Terminer** l’installation, un redémarrage d le **BizTalkServerApplication** et **BizTalkServerIsolatedHost** instances d’hôte.

Une fois installé, vous avez les éléments suivants :

- L’adaptateur LogicApp est ajouté à la console Administration de BizTalk.
- Le Gestionnaire d’envoi est créé et utilise l’hôte BizTalkServerApplication.
- Le Gestionnaire de réception est créé comme un service WCF et utilise l’hôte BizTalkServerIsolatedHost.
- Le `C:\Program Files (x86)\Microsoft BizTalk Server 2016\LogicApp Adapter` dossier est créé et inclut deux services : gestion et ReceiveService. 

    Le **gestion** est utilisé par le connecteur BizTalk dans une application logique pour se connecter à BizTalk Server à l’aide de la passerelle de données. Ce service de gestion permet à BizTalk Server recevoir des messages à partir d’une application Azure logique à l’aide de la passerelle de données. Ce service est uniquement utilisé sur le côté réception de BizTalk. Il n’est pas utilisé par le côté envoi.

    Le **ReceiveService** est utilisé par le connecteur BizTalk dans une application logique lorsque vous entrez l’emplacement de réception. Le **ReceiveService** est chargé d’envoyer les messages à partir de l’application logique. Ce service est uniquement utilisé sur le côté réception de BizTalk. Il n’est pas utilisé par le côté envoi.


### <a name="step-2-create-the-iis-applications"></a>Étape 2 : Créer les applications IIS

Les applications IIS utilisent les services de gestion et ReceiveService.

Vous pouvez exécuter les applications IIS à l’aide d’un nouveau pool d’applications, ou un pool d’applications existant. L’identité du pool d’applications nécessite l’appartenance aux groupes de mêmes que le compte qui exécute les services BizTalk, tels que les groupes d’utilisateurs d’applications BizTalk et utilisateurs d’hôtes BizTalk isolés.  

> [!TIP] 
> Si vous créez un nouveau pool d’applications, puis conserver la version du CLR .NET par défaut et le pipeline géré. N’oubliez pas, choisissez une identité qui a une appartenance aux groupes BizTalk mêmes que votre compte de service BizTalk (paramètres avancés). 

#### <a name="create-the-management-iis-application"></a>Créer l’application de gestion IIS
L’URL de cette application IIS est utilisée par le connecteur de BizTalk (dans votre application logique) pour utiliser la passerelle de données sur votre serveur BizTalk Server.

1. Ouvrez le Gestionnaire des Services (IIS) Internet.
2. Avec le bouton droit **Site Web par défaut**, et **ajouter Application**. Dans cette nouvelle application : 

    1. Entrez le **Alias** (nom) de votre application, tel que **IISLogicApp**. 
    2. **Sélectionnez** le pool d’applications.
    3. Définir le **chemin d’accès physique** à `C:\Program Files (x86)\Microsoft BizTalk Server 2016\LogicApp Adapter\Management`. 
    3. **Paramètres de test** pour confirmer le pool d’applications identité transmet l’authentification et autorisation des tests.

3. Sélectionnez **OK** pour enregistrer vos modifications.
4. Ouvrez un navigateur web et accédez à `http://localhost/YourApplicationAlias/schemas?api-version=2016-10-26`, tel que `http://localhost/IISLogicApp/Schemas?api-version=2016-10-26`. Une liste de schémas affichage, ou vous êtes invité à ouvrir/enregistrer `schemas.json`. Le résultat réel dépend de votre navigateur web. Si aucune de ces cas, puis votre identité de pool d’applications est absent l’appartenance aux groupes BizTalk.

#### <a name="create-the-biztalk-receiveservice-iis-application"></a>Créer l’application BizTalk ReceiveService IIS
L’URL de cette application IIS est utilisée par le connecteur BizTalk (dans votre application logique) lorsque vous choisissez l’emplacement de réception. 

1. Ouvrez le Gestionnaire des Services (IIS) Internet.
2. Avec le bouton droit **Site Web par défaut**, et **ajouter Application**. Dans cette nouvelle application : 

    1. Entrez le **Alias** (nom) de votre application, tel que **ReceiveWCFService**. 
    2. **Sélectionnez** le même pool d’applications en tant que l’application IIS précédente.
    3. Définir le **chemin d’accès physique** à `C:\Program Files (x86)\Microsoft BizTalk Server 2016\LogicApp Adapter\ReceiveService`. 
    3. **Paramètres de test** pour confirmer le pool d’applications identité transmet l’authentification et autorisation des tests.

3. Sélectionnez **OK** pour enregistrer vos modifications.


### <a name="step-3-create-a-logic-app"></a>Étape 3 : Créer une application de logique

1. Dans le [portail Azure](https://portal.azure.com), créer une application logique.
2. Ajouter le **HTTP lors de la demande est reçue** déclencheur.
3. Ajouter le **BizTalk Server - préparer un message à partir de JSON** action. 
4. **Facultatif**: sélectionnez **se connecter via une passerelle de données sur site**et entrez les informations suivantes : 

    | Propriété |  Description |
   | --- | --- |
    | URL de BizTalk Server | Entrez le nom de domaine complet (FQDN) de gestion BizTalk dans l’URL de l’application IIS. Par exemple, entrez `http://BizTalkServerName.corp.contoso.com/IISLogicApp/`. |
    | Type d’authentification | Sélectionnez **Windows**. |
   | Utilisateur | Entrez l’identité du pool d’applications IIS. |
   | Mot de passe | Entrez le mot de passe du pool d’applications IIS. |
   | Passerelle | Sélectionnez la passerelle que vous avez créé. |

    > [!TIP] 
    > N’oubliez pas, la passerelle de données est uniquement requis si :
    > - Vous utilisez un serveur de BizTalk sur site
    > - Vous utilisez un ordinateur virtuel de BizTalk Server Azure *et* la machine virtuelle n’est pas exposée comme un point de terminaison HTTP (aucune URL)

5. Sélectionnez **Créer**. 
6. Configuration de l’action. Pour **corps**, sélectionnez la sortie du corps HTTP. Pour **schéma**, sélectionnez le schéma que vous souhaitez utiliser. 

    > [!NOTE] 
    > Cette étape suppose que vous êtes familiarisé avec les schémas dans BizTalk Server et connaissez le schéma souhaité. Si vous n’êtes pas sûr, puis déployer l’exemple HelloWorld SDK, mettre à jour ses artefacts pour utiliser l’adaptateur de l’application logique et utiliser son message de schéma et des exemples. 

7. Ajouter une nouvelle étape, puis sélectionnez le **BizTalk Server - envoyer un message** action. Pour **un emplacement de réception**, sélectionnez l’URL dans la liste déroulante ou entrez le nom de domaine complet (FQDN) de l’URL d’application ReceiveService IIS. Par exemple, entrez `http://BizTalkServerName.corp.contoso.com/ReceiveWCFService/Service1.svc`.

    > [!TIP] 
    > Lorsque vous créez l’emplacement de réception, cette URL exacte devra également être entré dans les propriétés de transport de l’emplacement de réception en tant que le **adresse publique** (onglet Général).

    Pour **corps**, sélectionnez la corps de la sortie à partir de l’action précédente de BizTalk Server. 

8. **Enregistrer** vos modifications. 

Lorsque vous enregistrez, le déclencheur de la requête HTTP crée automatiquement une URL. Copiez cette URL ; vous en avez besoin dans **étape 5 : envoyer un message**.

### <a name="step-4-create-a-receive-port-and-a-receive-location"></a>Étape 4 : Créer un port de réception et un emplacement de réception

> [!NOTE] 
> Au lieu de créer votre propre réception ports et l’emplacement de réception, vous pouvez déployer l’exemple HelloWorld SDK. Mettre à jour les artefacts pour utiliser l’adaptateur Logic Apps. 
 
Cette section répertorie les étapes pour créer vos propres artefacts. 

1. Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez l’application que vous souhaitez Exécutez l’emplacement de réception. Par exemple, développez **BizTalk Application 1**.
2. Sélection de droite **Ports de réception**, sélectionnez **nouveau**, puis sélectionnez **Port de réception unidirectionnel**.
3. Dans les propriétés de Port de réception, entrez ce qui suit :  

    | Utiliser | Pour effectuer cette opération |
    | --- | --- |
    | **Nom** | Entrez un nom pour le port de réception. Par exemple, entrez **LAReceivePort**. |
    | **Authentification** | Options : <br/><ul><li>Aucune authentification : par défaut. Désactive l’authentification.</li><li>Supprimer les messages si l’authentification échoue : Active l’authentification, mais à de dépôt des messages non authentifiés.</li><li>Conserver les messages si l’authentification échoue : cliquez sur cette option pour activer l’authentification et conserver les messages non authentifiés. </li></ul>|
    | **Activer le routage des messages ayant échoué** | Achemine les messages ayant échoué le traitement vers une application abonnée (un autre planification d’orchestration ou le port de réception). Désactivez cette option pour interrompre les messages ayant échoué et générer un accusé de réception négatif (NACK). Par défaut, cette case à cocher est désactivée. Pour plus d’informations, consultez [comment activer le routage de Messages a échoué pour un Port de réception](../core/how-to-enable-routing-for-failed-messages-for-a-receive-port.md).|

4. Sélectionnez **emplacements de réception**, puis sélectionnez **nouveau**. 
5. Entrez un **nom** pour l’emplacement de réception. Par exemple, entrez **LAReceiveLoc**.
6. Pour le **Type**, sélectionnez **LogicApp** à partir de la liste, puis sélectionnez le **bouton Configurer**. 
7. Dans le **général** onglet, configurez l’adresse de point de terminaison pour votre application logique :

    | Utiliser | Pour effectuer cette opération |
    | --- | --- |
    | **Adresse (URI)** | Obligatoire. Entrez l’URL de l’application BizTalk ReceiveService IIS (`/YourIISApp2Name/Service1.svc`). Par exemple, entrez `/ReceiveWCFService/Service1.svc`. |
    | **Adresse publique** | Obligatoire. Entrez `http://<your fully qualified machine name>/YourIISApp2Name/Service1.svc`. Par exemple, entrez `http://btsProd.northamerica.corp.contoso.com/ReceiveWCFService/Service1.svc`. <br/><br/>Cette URL exacte est également répertorié dans votre logique d’application dans l’emplacement de réception.|

8. **Facultatif**. Dans le **liaison** onglet, configurez un délai d’attente ainsi que relatives au codage des propriétés de la liaison WCF-WebHttp sous-jacente. Ces propriétés sont utiles lorsque vous traitez des messages volumineux.

    | Utiliser | Pour effectuer cette opération |
    | --- | --- |
    | Délai d’attente ouverte | Entrez l’intervalle de temps que nécessaire pour l’opération d’ouverture du canal. Cette valeur doit être supérieure ou égale à System.TimeSpan.Zero. <br/><br/>Valeur par défaut : 00:01:00<br/>Valeur maximale : 23:59:59. |
    | Un délai d’envoi |Entrez l’intervalle de temps que nécessaire pour l’opération d’envoi. Cette valeur doit être supérieure ou égale à System.TimeSpan.Zero. Si vous utilisez une requête-réponse port de réception, cette valeur spécifie un intervalle de temps pour l’ensemble de l’interaction se termine, même si le client renvoie un message volumineux. <br/><br/>Valeur par défaut : 00:01:00<br/>Valeur maximale : 23:59:59.|
    | Délai d’attente Close | Entrez l’intervalle de temps que nécessaire pour l’opération de fermeture du canal. Cette valeur doit être supérieure ou égale à System.TimeSpan.Zero. <br/><br/>Valeur par défaut : 00:01:00<br/>Valeur maximale : 23:59:59. |
    | Taille maximale des messages reçus (octets) | Entrez la taille maximale, en octets, d’un message, y compris les en-têtes, doit être reçu sur le câble. La taille des messages est liée par la quantité de mémoire allouée à chaque message. Vous pouvez vous servir de cette propriété afin de limiter les expositions aux attaques de type refus de service. <br/><br/>Valeur par défaut : 65536<br/>Valeur maximale : 2147483647|
    | Nombre maximum d'appels simultanés | Entrez le nombre d’appels simultanés à une instance de service unique. Les appels excédentaires sont mis en file d'attente. La valeur 0 est équivalente à la définition à Int32.MaxValue. <br/><br/>La valeur par défaut est 200.|

9. **Facultatif**. Dans le **sécurité** onglet, configurez les propriétés de sécurité. À des fins de développement, vous pouvez sélectionner aucune :

    | Utiliser | Pour effectuer cette opération |
    | --- | --- |
    | Mode de sécurité | Options :  <br/><br/><ul><li>None : Les Messages ne sont pas sécurisés pendant le transfert.</li><li>Transport : La sécurité est fournie en utilisant le transport HTTPS. Les messages SOAP sont sécurisés à l'aide de HTTPS. Pour utiliser ce mode, vous devez définir des couche SSL (Secure Sockets) dans Internet Information Services (IIS). </li><li>TransportCredentialOnly : par défaut. </li></ul> |
    | Types d’informations d’identification du client de transport | Choisissez le type d’informations d’identification lors de l’utilisation de l’authentification du client. Options :  <br/><br/><ul><li>None : Aucune authentification se produit au niveau du transport.</li><li>Basic : Utilise l’authentification de base pour envoyer les noms d’utilisateur et mots de passe en texte brut sur le réseau. Vous devez créer les comptes d'utilisateur de domaine ou locaux correspondant aux informations d'identification.</li><li>Digest : Utilise l’authentification Digest pour envoyer des mots de passe sous la forme d’une valeur de hachage sur le réseau. Disponible uniquement sur les domaines avec contrôleurs de domaine d’authentification de systèmes d’exploitation Windows Server en cours d’exécution. Vous devez créer les comptes d'utilisateur de domaine ou locaux correspondant aux informations d'identification du client.</li><li>NTLM : par défaut. Les clients envoie les informations d’identification sans envoyer un mot de passe à cet emplacement de réception. Vous devez créer les comptes d'utilisateur de domaine ou locaux correspondant aux informations d'identification du client.</li><li>Windows : L’authentification intégrée Windows négocie Kerberos ou NTLM, préférant Kerberos si un domaine est présent. Pour utiliser Kerberos, il est important pour que le client d’identifier le service avec un nom de principal du service (SPN). Vous devez créer les comptes d'utilisateur de domaine ou locaux correspondant aux informations d'identification du client.</li><li>Certificat : Utilise un certificat client. La chaîne de certificats d’autorité de certification pour les certificats X.509 du client doivent être installés dans le magasin de certificats Autorités de Certification racines de confiance de cet ordinateur afin que les clients peuvent s’authentifier à cet emplacement de réception.</li><li>InheritedFromHost</li></ul> |
    | Utiliser l’authentification unique | |


10. **Facultatif**. Dans le **Messages** onglet, utilisez la **en-têtes HTTP sortants** propriété à ajouter tous les en-têtes personnalisés, utilisez les propriétés supplémentaires pour aider à erreurs : 

    | Utiliser | Pour effectuer cette opération |
    | --- | --- |
    |En-têtes HTTP sortants | Entrez les en-têtes HTTP que vous souhaitez utiliser sur le message de réponse. | 
    | Désactiver l'emplacement en cas d'échec | Désactive l’emplacement de réception si le traitement entrant échoue en raison d’une erreur de pipeline de réception ou un échec de routage. Valeur par défaut est désactivée.|
    | Suspendre le message de requête en cas d'échec | Suspend le message de demande si le traitement entrant échoue en raison d’une erreur de pipeline de réception ou un échec de routage. Valeur par défaut est désactivée.|
    | Inclure le détail des exceptions dans les messages d'erreur | Lorsqu’une erreur se produit, retourne des erreurs SOAP pour le débogage de l’aide. Valeur par défaut est désactivée.|

[Gestion des emplacements de réception](../core/managing-receive-locations.md) décrit les propriétés supplémentaires. 

### <a name="step-5-send-a-message"></a>Étape 5 : Envoyer un message

1. Ouvrez Fiddler ou Postman (ou tout ce que vous préférez).
2. Collez l’URL du déclencheur demande à partir de votre application logique. Cette URL est copiée à l’étape 3. 
3. Sélectionnez **POST** en tant que le verbe HTTP et le jeu le **Content-type** en-tête `application/json`. Dans le corps, collez le texte JSON suivant :  

    ```json
    {“hello”:”world”}
    ```

4. Comme il s’agit d’un appel à sens unique à BizTalk Server, le résultat doit être un HTTP 202. Si vous utilisez l’exemple HelloWorld SDK, accédez à votre serveur BizTalk server. Il peut être un fichier dans votre dossier d’envoi. 


## <a name="send-messages-to-a-logic-app"></a>Envoyer des messages à une application de logique

### <a name="step-1-install-the-logic-apps-adapter"></a>Étape 1 : Installer l’adaptateur Logic Apps

L’adaptateur Logic Apps est disponible en téléchargement séparé et n’est pas inclus dans l’installation de BizTalk Server.

1. Accédez à [l’adaptateur Microsoft BizTalk Server pour les applications de la logique de](https://www.microsoft.com/download/details.aspx?id=54287)et l’enregistrer. 
2. Ouvrez le LogicAppAdapter.iso, puis exécutez le **LogicApp Adapter.msi** fichier à installer.
3. **Terminer** l’installation, puis redémarrer le **BizTalkServerApplication** et **BizTalkServerIsolatedHost** instances d’hôte.

Une fois installé, vous avez les éléments suivants :

- L’adaptateur LogicApp est ajouté à la console Administration de BizTalk
- Le Gestionnaire d’envoi est créé et utilise l’hôte BizTalkServerApplication.
- Le Gestionnaire de réception est créé comme un service WCF et utilise l’hôte BizTalkServerIsolatedHost.
- Le `C:\Program Files (x86)\Microsoft BizTalk Server 2016\LogicApp Adapter` dossier est créé et inclut deux services : gestion et ReceiveService. Ces services ne sont pas utilisés pour envoyer des messages à une application logique. 


### <a name="step-2-create-a-logic-app"></a>Étape 2 : Créer une application de logique

1. Dans le [portail Azure](https://portal.azure.com), créer une application logique.
2. Ajouter le **HTTP lors de la demande est reçue** déclencheur
3. Ajouter le **Outlook Office 365 - envoyer un e-mail** action. Pour le **à** d’adresses, entrez votre adresse d’Office 365. Pour le **sujet**, entrez `Sending from BizTalk`. Pour **corps**, choisissez le *corps* de sortie à partir de la **HTTP lors de la demande est reçue** déclencheur. 
4. Votre application logique est similaire à : 

    ![LogicAppExample](../core/media/logicappexample.gif)

5. Copiez l’URL HTTP POST qui est créé automatiquement lorsque vous enregistrez l’application logique ; vous avez besoin de cette URL dans l’étape suivante. Vous devrez peut-être fermer et rouvrir l’application logique pour afficher l’URL.  


### <a name="step-3-create-a-send-port"></a>Étape 3 : Créer un Port d’envoi

Pour envoyer des messages à une application de la logique de BizTalk Server, l’application logique doit avoir un **manuel** déclencher, telles que **manuel - demande de lorsque HTTP est reçue**. 

1. Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez l’application que vous souhaitez Exécutez le port d’envoi. Par exemple, développez **BizTalk Application 1**.
2. Sélection de droite **Ports d’envoi**, sélectionnez **nouveau**, puis sélectionnez **Port d’envoi unidirectionnel statique**.
3. Entrez un **nom** pour le port d’envoi. Par exemple, entrez **LASendPort**.
4. Pour le **Type**, sélectionnez **LogicApp** à partir de la liste, puis sélectionnez le **configurer** bouton. 
5. Dans le **général** onglet, configurez le **URI de rappel** de votre déclencheur d’application logique. Pour ce faire, deux possibilités s'offrent à vous : 

    **Option 1** : collez l’URL de POST HTTP que vous avez copié à l’étape précédente dans le **déclencheur (URI de rappel)** propriété. Vous pouvez également copier l’URI en procédant comme suit :  
  
      1. Dans le [portail Azure](https://portal.azure.com), ouvrez votre application de logique dans le Concepteur de Logic Apps (mode édition). 
      2. Sélectionnez le **HTTP lors de la demande est reçue** de la carte, puis copiez le **URL**. 
      3. Dans votre port d’envoi, collez l’URL dans le **déclencheur (URI de rappel)** propriété.

    > [!TIP] 
    > Vous pouvez également utiliser votre API de gestion pour obtenir cet URI.

    **Option 2** : Si vous ne connaissez pas l’URI de rappel pour votre déclencheur, sélectionnez **configurer**et connectez-vous à Azure. Puis, utilisez les listes déroulantes pour sélectionner votre **abonnement**, **groupe de ressources**, **application logique**, et **déclencheur**.
 
6. **Facultatif**. Dans le **liaison** onglet, configurez un délai d’attente ainsi que relatives au codage des propriétés de la liaison WCF-WebHttp sous-jacente. Ces propriétés sont utiles lorsque vous traitez des messages volumineux.

    | Utiliser | Pour effectuer cette opération |
    | --- | --- |
    | Délai d’attente ouverte | Entrez l’intervalle de temps que nécessaire pour l’opération d’ouverture du canal. Cette valeur doit être supérieure ou égale à System.TimeSpan.Zero. <br/><br/>Valeur par défaut : 00:01:00<br/>Valeur maximale : 23:59:59. |
    | Un délai d’envoi |Entrez l’intervalle de temps que nécessaire pour l’opération d’envoi. Cette valeur doit être supérieure ou égale à System.TimeSpan.Zero. Si vous utilisez une requête-réponse port de réception, cette valeur spécifie un intervalle de temps pour l’ensemble de l’interaction se termine, même si le client renvoie un message volumineux. <br/><br/>Valeur par défaut : 00:01:00<br/>Valeur maximale : 23:59:59.|
    | Délai d’attente Close | Entrez l’intervalle de temps que nécessaire pour l’opération de fermeture du canal. Cette valeur doit être supérieure ou égale à System.TimeSpan.Zero. <br/><br/>Valeur par défaut : 00:01:00<br/>Valeur maximale : 23:59:59. |
    | Taille maximale des messages reçus (octets) | Entrez la taille maximale, en octets, d’un message, y compris les en-têtes, doit être reçu sur le câble. La taille des messages est liée par la quantité de mémoire allouée à chaque message. Vous pouvez vous servir de cette propriété afin de limiter les expositions aux attaques de type refus de service. <br/><br/>L’adaptateur d’appa logique tire parti du [classe WebHttpBinding](https://msdn.microsoft.com/library/system.servicemodel.webhttpbinding.aspx) dans le mode de transfert mis en mémoire tampon pour communiquer avec un point de terminaison. Pour le mode de transport de mise en mémoire tampon, la [WebHttpBinding.MaxBufferSize](https://msdn.microsoft.com/library/system.servicemodel.webhttpbinding.maxbuffersize.aspx) propriété est toujours égale à la valeur de cette propriété.  <br/><br/>Valeur par défaut : 65536<br/>Valeur maximale : 2147483647 |


7. **Facultatif**. Dans le **Messages** onglet, utilisez la **en-têtes HTTP sortants** propriété à ajouter tous les en-têtes personnalisés sur le message sortant. 
8. Sélectionnez **OK** pour enregistrer votre configuration. 

[La gestion des Ports d’envoi et groupes de ports d’envoi](../core/managing-send-ports-and-send-port-groups.md) décrit les propriétés de port d’envoi supplémentaires. 

### <a name="step-4-send-some-messages"></a>Étape 4 : Envoyer des messages

Vous pouvez créer un port de réception et l’emplacement de réception à l’aide de l’adaptateur File. Assurez-vous que votre application logique est activée.

1. Créer un port de réception, tel que *FileSendPort*,
2. Créer un emplacement de réception et définir les propriétés similaire à :  

    | Propriété | Exemple d’entrée |
    | --- | --- |
   | Dossier de réception | C:\temp\In\ |
   | Masque de fichier | *.txt |
   | Pipeline | PassThruReceive |

3. Dans le port d’envoi créé, définissez le **filtre** à :

    | Propriété | Opérateur | Valeur |
    | --- | --- | --- |
    | BTS.ReceivePortName |  == | *FileSendPort* |

4. Créer un fichier texte (nom_fichier.txt) avec le texte suivant. Utilisez ce fichier texte en tant que votre exemple de message : 

    ```
    <Data>
      <DataID>DataID_0</DataID>
      <DataDetails>DataDetails_0</DataDetails>
    </Data>
    ```

5. Copiez votre exemple de message (nom_fichier.txt) dans le dossier de réception. Le port d’envoi envoie le fichier .txt à l’application logique à l’aide de l’URI que vous avez entré. Votre application logique recevoir les fichiers. Si vous avez utilisé le connecteur Outlook Office 365, votre *à* adresse de messagerie doit recevoir le courrier électronique, avec l’exemple de message.

## <a name="next"></a>Suivant
[Quelles sont les applications logique](https://azure.microsoft.com/documentation/articles/app-service-logic-what-are-logic-apps/)  

[Créer une application de logique](https://azure.microsoft.com/documentation/articles/app-service-logic-create-a-logic-app/)

[À l’aide des adaptateurs dans BizTalk Server](../core/using-adapters.md)