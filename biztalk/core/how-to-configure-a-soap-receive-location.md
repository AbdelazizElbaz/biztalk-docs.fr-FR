---
title: "Pour configurer un protocole SOAP emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [SOAP adapters], virtual directories
- SOAP adapters, code samples
- configuring [SOAP adapters], receive locations
- virtual directories, SOAP adapters
- SOAP adapters, receive locations
- code samples, SOAP adapters
- configuring [SOAP adapters], code samples
- SOAP adapters, virtual directories
- receive locations, SOAP adapters
ms.assetid: 7e348409-9181-47e4-b3c0-c73eb2acffa3
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b33886296441082ea7d7e83b92659f81140d71f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-soap-receive-location"></a>Configuration d'un emplacement de réception SOAP
Vous pouvez configurer un emplacement de réception SOAP soit par programme soit à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 **Comment faire pour configurer un emplacement de réception SOAP par programme**  
  
 L’Explorateur BizTalk de modèle d’objet vous permet de créer et configurer les emplacements de réception par programmation. Le modèle d’objet de l’Explorateur BizTalk expose le**IReceiveLocation** emplacement interface de configuration de recevoir un **TransportTypeData** propriété en lecture/écriture. Cette propriété accepte le jeu de propriétés de configuration de l'emplacement de réception SOAP sous la forme d'une chaîne XML composée d'une paire nom/valeur. Pour définir cette propriété dans le modèle d’objet de l’Explorateur BizTalk, vous devez définir le **InboundTransportLocation** propriété de la **IReceiveLocation** interface.  
  
 Le **TransportTypeData** propriété de la **IReceiveLocation** interface n’a pas à définir. Dans ce cas, l'adaptateur SOAP utilise les valeurs par défaut pour la configuration de l'emplacement de réception SOAP, comme indiqué dans le tableau suivant.  
  
 Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir dans le modèle objet de l'Explorateur BizTalk pour l'emplacement de réception SOAP.  
  
|Nom de la propriété|Type| Description|  
|-------------------|----------|-----------------|  
|**URI**|Chaîne|Répertoire virtuel contenant le service Web sur le serveur de déploiement.|  
|**AddressableURI**|Chaîne|Champ d'adresse publique contenant l'URL entière pouvant être appelée.<br /><br /> Valeur par défaut : vide|  
|**UseSSO**|Booléen|Spécifie si l'adaptateur SOAP émet le ticket d'authentification unique pour les messages arrivant sur cet emplacement de réception.<br /><br /> Valeur par défaut : False|  
  
 Pour définir les propriétés, utilisez le format suivant :  
  
```  
receiveLocation.TransportTypeData = "<CustomProps><UseSSO vt=\"11\">-1</UseSSO></CustomProps>";  
```  
  
 Le **URI** et **AddressableURI** propriétés sont définies à l’aide de la **adresse** et **PublicAddress** propriétés de l’emplacement de réception objet.  
  
 Le fragment de code suivant illustre la création d'un emplacement de réception SOAP :  
  
```  
// Use BizTalk Explorer object model to create new SOAP receive location.  
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
//requires project reference to \Program Files\Microsoft BizTalk Server 2009\Developer Tools\Microsoft.BizTalk.ExplorerOM.dll  
BtsCatalogExplorer explorer = new Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer();  
explorer.ConnectionString = connectionString;  
  
// Add a new Request-Response port  
ReceivePort receivePort = explorer.AddNewReceivePort(true);  
receivePort.Name = "SampleReceivePort";  
receivePort.SendPipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruTransmit"];  
  
// Add primary SOAP receive location  
ReceiveLocation receiveLocation = receivePort.AddNewReceiveLocation();  
receiveLocation.Name = "SampleReceiveLocation";  
receiveLocation.Address = "/PurchaseOrder/POOrchestration.asmx";  
receiveLocation.TransportType = explorer.ProtocolTypes["SOAP"];  
receiveLocation.TransportTypeData = "<CustomProps><UseSSO vt=\"11\">-1</UseSSO></CustomProps>";  
receiveLocation.ReceivePipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruReceive"];  
foreach (ReceiveHandler receiveHandler in explorer.ReceiveHandlers)  
{  
if (receiveHandler.TransportType.Name == receiveLocation.TransportType.Name)  
{  
receiveLocation.ReceiveHandler = receiveHandler;   
}  
}  
  
// Save  
explorer.SaveChanges();   
```  
  
 **Comment configurer un protocole SOAP emplacement de réception avec la Console Administration de BizTalk Server**  
  
 Vous pouvez définir des variables d'adaptateur d'emplacement de réception SOAP dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Si les propriétés ne sont pas définies pour l'emplacement de réception, les valeurs par défaut du gestionnaire de réception définies dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont utilisées.  
  
> [!NOTE]
>  Avant d'effectuer les procédures suivantes, vous devez avoir ajouté un port de réception. Pour plus d’informations, consultez [la création d’un Port de réception](../core/how-to-create-a-receive-port.md).  
  
### <a name="to-configure-variables-for-a-soap-receive-location"></a>Pour configurer les variables pour un emplacement de réception SOAP  
  
1.  Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez le vous souhaitez créer un emplacement de réception dans l’application.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, dans le volet gauche, cliquez sur le **Port de réception** nœud. Dans le volet droit, cliquez avec le bouton droit sur le port de réception associé à un emplacement de réception existant ou auquel associer un nouvel emplacement, puis cliquez sur **Propriétés**.  
  
3.  Dans le **propriétés du Port de réception** boîte de dialogue, dans le volet gauche, sélectionnez **emplacements de réception**, puis dans le volet droit, double-cliquez sur un existant emplacement de réception ou cliquez sur **nouveau**pour créer un nouvel emplacement de réception.  
  
4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** section regard **Type**, sélectionnez **SOAP** dans la liste déroulante, puis cliquez sur **configurer**.  
  
5.  Dans le **propriétés du Transport SOAP** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Répertoire virtuel assorti de fichier .asmx du Service Web**|Indiquer le fichier .asmx créé par l'Assistant Publication de services Web de BizTalk.<br /><br /> Le format de ce message est similaire à ce qui suit :<br /><br /> /BonDeCommande/OrganisationBDC.asmx<br /><br /> Où l'emplacement complet du fichier .asmx est http://localhost/BonDeCommande/OrchestrationBDC.asmx. **Remarque :** l’URI pour un envoi de port ou de réception emplacement ne peut pas dépasser 256 caractères.|  
    |**Adresse publique**|Indiquer l'adresse URI complète de cet emplacement de réception. La valeur de cette propriété est constituée du nom du serveur et de celui du répertoire virtuel. L'URI indiquée doit désigner l'URL du site Web public de manière à ce que les partenaires commerciaux puissent s'y connecter lors de l'envoi de messages à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].<br /><br /> Ces informations sont facultatives et ne sont pas utilisées par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ce paramètre est disponible pour permettre aux administrateurs de documenter l'URL publique à laquelle est lié l'emplacement de réception.|  
    |**Utiliser l’authentification unique**|Indiquer que l'adaptateur SOAP utilise l'authentification unique de l'entreprise. **Remarque :** l’Assistant de publication des Services Web BizTalk vous permet d’utiliser SharePoint Portal Server Single Sign-On ; cette propriété active seulement Enterprise Single Sign-On.|  
  
6.  Cliquez sur **OK**.  
  
7.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, entrez les valeurs appropriées pour terminer la configuration de l’emplacement de réception, puis cliquez sur **OK** pour enregistrer les paramètres. Pour plus d’informations sur la **propriétés des emplacements de réception** boîte de dialogue, consultez [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).  
  
 Les paramètres de sécurité utilisés par l'emplacement de réception SOAP sont définis dans IIS. Par défaut, l'emplacement de réception SOAP n'est pas configuré pour utiliser l'authentification anonyme.  
  
 Tandis que le client SOAP appelle le service Web, l'adaptateur SOAP authentifie le client à l'aide de l'authentification Anonyme, De base, Digest ou Intégrée Windows. Si la vérification de l'utilisateur est activée, le contexte utilisateur est transmis au gestionnaire de réception.  
  
> [!NOTE]
>  Toute configuration IIS menant au partage du même processus par SOAP et HTTP est non valide. Vous ne pouvez utiliser qu'un seul récepteur isolé par processus.  
  
### <a name="to-update-a-virtual-directory-to-use-aspnet-40"></a>Pour mettre à jour un répertoire virtuel pour utiliser ASP.NET 4.0  
  
1.  Lancez le Gestionnaire des services Internet (IIS). Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
2.  Si vous avez besoin pour se connecter à un serveur IIS distant, bouton droit sur le **Internet Information Services** nœud, puis cliquez sur **connexion**.  
  
3.  Tapez le nom d'ordinateur du serveur IIS distant et les informations d'identification, le cas échéant.  
  
4.  Développez le nom du serveur qui héberge le site Web ou le répertoire virtuel à mettre à jour.  
  
5.  Développez **Sites**.  
  
6.  Développez **Site Web par défaut**.  
  
7.  Développez le site Web par défaut pour afficher les répertoires virtuels sous le site Web.  
  
8.  Cliquez sur le répertoire virtuel que vous souhaitez mettre à jour pour utiliser ASP.NET 4.0, cliquez sur **gérer l’Application**, puis cliquez sur **paramètres avancés**. Le **Pool d’applications** champ affiche le pool d’applications défini pour le répertoire virtuel sélectionné. Cliquez sur **OK**.  
  
9. Dans la fenêtre Gestionnaire des Services Internet (IIS), cliquez sur **Pools d’applications**. Le volet Détails affiche la liste des pools d'applications sur le serveur.  
  
10. Cliquez sur le pool d’applications défini à l’étape 8, puis cliquez sur **les paramètres de base**.  
  
11. Dans le **modifier le Pool d’applications** boîte de dialogue zone, modifier les paramètres suivants :  
  
    -   **Version du .NET framework** à **4.0**  
  
    -   **Mode pipeline géré** à **classique**  
  
12. Cliquez sur **OK** pour appliquer les modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de Services Web](../core/consuming-web-services.md)