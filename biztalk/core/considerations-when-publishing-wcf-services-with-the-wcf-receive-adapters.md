---
title: "Considérations relatives à la publication de Services WCF avec WCF des adaptateurs de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing, WCF services
- WCF adapters, best practices
- WCF adapters, receive adapters
- WCF services, publishing
- best practices, WCF adapters
ms.assetid: 797b7ffd-534c-4f09-9738-fb17b208bc96
caps.latest.revision: "34"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30175e7966d565306c45820f1a6c2e22e4611876
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters"></a>Considérations relatives à la publication de services WCF à l'aide des adaptateurs de réception WCF
Cette rubrique fournit des informations à prendre en compte lors de la publication des services WCF à l'aide des adaptateurs de réception WCF.  La publication d'un service à l'aide d'un adaptateur WCF permet son appel par un client WCF comme s'il s'agissait d'un service WCF classique.  
  
## <a name="in-process-hosting"></a>Hébergement in-process  
 L'hébergement de l'emplacement de réception dans l'espace de processus [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], btsntsvc.exe, offre les avantages d'un développement et d'un déploiement simplifiés. En outre, il crée plus d'instances d'hôte que l'hébergement dans IIS afin de bénéficier de la haute disponibilité et des fonctionnalités d'équilibrage de charge de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  Pour plus d’informations d’hébergement en dehors de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] faire des processus dans IIS [de configurer IIS pour les adaptateurs de réception WCF isolés](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md).  
  
## <a name="set-the-isoneway-property-of-wcf-services-published-with-the-wcf-adapters-except-for-the-wcf-netmsmq-receive-adapter-to-false"></a>Définition sur false de la propriété IsOneWay des services WCF publiés à l'aide des adaptateurs WCF (à l'exception de l'adaptateur de réception WCF-NetMsmq)  
 Le **System.ServiceModel.OperationContractAttribute.IsOneWay** propriété des services WCF publiés avec les adaptateurs WCF, à l’exception des services publiés avec WCF-NetMsmq où elle est définie sur l’adaptateur de réception **true**  , a la valeur **false** même pour les emplacements de réception l’unidirectionnels. Si le **IsOneWay** est définie sur **false**, même les méthodes qui retournent un **void** génèrent un message de réponse. Dans ce cas, l'infrastructure crée et envoie un message vide pour indiquer à l'appelant que la méthode est renvoyée. Grâce à cette approche, l'infrastructure peut renvoyer au client des exceptions générées par l'opération du service.  
  
 Pour consommer des services WCF publiés avec les adaptateurs WCF (sauf l’adaptateur de réception WCF-netmsmq) dans lequel **IsOneWay** est **false**, le **IsOneWay** propriété sur le côté client doit être définie sur **false** comme suit :  
  
```  
[ServiceContract(Namespace="Microsoft.WCF.Documentation")]  
  public interface ISampleService{  
    [OperationContract(IsOneWay=false, ReplyAction="*",Action="…"]  
    string SampleMethod(string msg);  
}  
```  
  
> [!NOTE]
>  Étant donné que la valeur par défaut de la **IsOneWay** propriété **false**, vous n’êtes pas obligé de spécifier la propriété dans le code.  
  
## <a name="the-replyaction-property-of-the-operationcontractattribute-on-the-client-side-should-be-set-to--an-asterisk-when-consuming-wcf-services-published-with-one-way-receive-locations"></a>La propriété ReplyAction de OperationContractAttribute côté client doit être définie sur « * » (astérisque) lors de l'utilisation de services WCF publiés à l'aide d'emplacements de réception unidirectionnels  
 Le **System.ServiceModel.OperationContractAttribute.ReplyAction** propriété de la **System.ServiceModel.OperationContractAttribute** peut être utilisé côté client pour spécifier la valeur de la Action SOAP pour les messages de réponse des services WCF.  
  
 En plus d'attribuer une valeur particulière à l'en-tête d'action du message de réponse (pour informer le client qu'il s'agit d'une réponse et lui indiquer l'action à effectuer), vous pouvez spécifier la chaîne « * » (astérisque). Dans une application cliente, cet astérisque permet de demander au client de ne pas valider l'action de réponse dans les messages de réponse envoyés par le service.  
  
 Pour consommer un service WCF service publié par unidirectionnel emplacement de réception, la méthode proxy pour le service WCF doit retourner **void**, auquel cas la méthode proxy attend que le service WCF envoie un message vide pour indiquer à l’appelant qui la méthode est renvoyée. Pour la méthode proxy reçoive ce message vide, le **ReplyAction** propriété de la **OperationContractAttribute** doit être défini sur « * » (astérisque) comme suit :  
  
```  
[ServiceContract(Namespace="Microsoft.WCF.Documentation")]  
  public interface ISampleService{  
    [OperationContract(IsOneWay=false, ReplyAction="*",Action="…"]  
    string SampleMethod(string msg);  
}  
```  
  
> [!NOTE]
>  Vous n’êtes pas obligé de définir le **ReplyAction** propriété »\*» (astérisque) pour l’adaptateur WCF-NetMsmq, car l’adaptateur WCF-NetMsmq requiert les clients WCF définir le **IsOneWay** propriété **true**.  
  
## <a name="an-isolated-host-instance-can-run-only-one-adapter"></a>Une instance d'hôte isolé ne peut exécuter qu'un seul adaptateur  
 Une instance d'hôte isolé ne peut exécuter qu'un seul adaptateur. Si vous configurez les gestionnaires de réception de plusieurs adaptateurs isolés, tels que des adaptateurs HTTP, SOAP et WCF, avec un seul hôte isolé, vous devez créer plusieurs pools d'applications, soit un pool d'applications par adaptateur. Pour plus d’informations sur les hôtes BizTalk isolé, consultez [activation des Services Web](../core/enabling-web-services.md).  
  
## <a name="use-the-template----content-specified-by-template-option-when-sending-non-xml-content-as-response-messages"></a>Utilisation de l'option « Modèle -- contenu spécifié par le modèle » lors de l'envoi de contenu non-XML en tant que messages de réponse  
 Les adaptateurs WCF avec **corps--corps du message de réponse BizTalk** (la valeur par défaut) option n’autorisent pas l’envoi de messages non-XML tels que des images bitmap et des données de caractères. Vous pouvez utiliser la **modèle--contenu spécifié par le modèle** option pour les adaptateurs WCF envoyer des messages non XML. Pour plus d’informations sur la façon d’utiliser le modèle, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).  
  
## <a name="setting-up-the-permissions-for-a-wcf-service-published-with-the-wcf-service-publishing-wizard"></a>Configuration des autorisations pour un service WCF publié à l'aide de l'Assistant Publication de services WCF  
 Lors de l'utilisation d'applications ASP.NET créées à l'aide de l'Assistant Publication de services WCF sur la plateforme [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], des erreurs relatives à l'accès aux DLL lors de l'appel du service WCF peuvent se produire. Ces erreurs sont généralement associées aux problèmes liés à la sécurité par défaut sous [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] et [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]. Pour plus d’informations sur ces erreurs, consultez l’article Microsoft Help and Support intitulé « You Receive a « System.IO.FileNotFoundException » erreur lorsque le Client Application appelle un Service Web » sur le site Web aide et Support [http:// go.Microsoft.com/fwlink/ ? LinkId = 43659](http://go.microsoft.com/fwlink/?LinkId=43659).  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requiert que le processus exécutant le service WCF dispose des autorisations appropriées si un hôte in-process ou un hôte isolé exécute le service. Sous [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] et [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], le groupe Windows par défaut pour les hôtes isolés est le Groupe d'utilisateurs d'hôtes isolés. Ainsi, l'ajout des autorisations au Groupe d'utilisateurs d'hôtes isolés devrait résoudre ce problème.  
  
#### <a name="to-add-the-permissions-to-the-isolated-host-users-group"></a>Pour ajouter les autorisations au Groupe d'utilisateurs d'hôtes isolés  
  
1.  Dans l'Explorateur Microsoft Windows, localisez le répertoire % windir%\temp.  
  
2.  Cliquez sur % windir%\temp, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés** boîte de dialogue, cliquez sur le **sécurité** onglet.  
  
4.  Cliquez sur **ajouter**, sélectionnez **le groupe utilisateurs d’hôtes isolés**, puis cliquez sur **OK**.  
  
## <a name="setting-up-the-permissions-for-a-wcf-receive-location-with-the-wcf-netmsmq-adapter"></a>Configuration des autorisations pour un emplacement de réception WCF à l'aide de l'adaptateur WCF-NetMsmq  
 Lorsqu'un client WCF utilisant NetMsmqBinding envoie un message à un service WCF publié à l'aide de l'adaptateur WCF-NetMsmq, il adresse le message à la file d'attente cible, qui est la file d'attente gérée par le gestionnaire de files d'attente du service. Le gestionnaire de files d'attente sur le client envoie le message à une file d'attente de transmission (ou sortante). La file d'attente de transmission est une file d'attente, située sur le gestionnaire de files d'attente côté client, qui stocke des messages pour les transmettre à la file d'attente cible.  
  
 Le gestionnaire de files d'attente du service accepte des messages adressés aux files d'attente cibles qu'il possède et stocke les messages. Ensuite, le service lance des demandes de lecture à partir de la file d'attente cible. Le gestionnaire de files d'attente livre alors les messages au service. C'est la raison pour laquelle le compte de service pour l'instance d'hôte BizTalk hébergeant l'emplacement de réception doit disposer des autorisations de lecture à partir de la file d'attente cible.  
  
## <a name="use-an-empty-body-path-expression-to-receive-a-soap-message-with-character-data-in-the-content-of-the-soap-body-element"></a>Utilisation d'une expression de chemin de corps vide pour recevoir un message SOAP contenant des données de type caractère dans l'élément SOAP Body  
 Pour un service WCF de réception pour créer un message BizTalk à partir d’un message de réponse entrante avec des données de caractères dans le contenu de SOAP **corps** élément, comme indiqué dans l’exemple suivant, vous devez laisser le **le chemin du corps expression** zone de texte vide sur le **Message** onglet dans la boîte de dialogue Propriétés du transport WCF adaptateur.  
  
```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      ...  
    </s:Header>  
    <s:Body>Contoso</s:Body>  
</s:Envelope>  
```  
  
 Si vous sélectionnez le **enveloppe** ou **corps** option, l’adaptateur ne peut pas créer le message BizTalk à partir du précédent message entrant. Le message n'est pas interrompu car les messages échouant au cours du traitement de marshaling SOAP entrant ne sont pas interrompus. Pour plus d’informations sur l’utilisation de l’expression de chemin de corps sur le **Message** , consultez la rubrique [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).  
  
> [!NOTE]
>  Vous pouvez utiliser l'outil TraceViewer (SvcTraceViewer.exe) du Kit de développement Windows SDK en configurant le fichier BTSNTSvc.exe.config. Pour plus d’informations sur le Kit de développement logiciel Windows, consultez « Nouveautés dans le Kit de développement logiciel Windows » à [http://go.microsoft.com/fwlink/?LinkId=75219](http://go.microsoft.com/fwlink/?LinkId=75219). Pour plus d’informations sur l’outil TraceViewer, consultez « TraceViewer Tool (SvcTraceViewer.exe) » à [http://go.microsoft.com/fwlink/?LinkId=75218](http://go.microsoft.com/fwlink/?LinkId=75218).  
  
## <a name="using-schemas-that-reference-other-schemas"></a>Utilisation des schémas faisant référence à d'autres schémas  
 Vous pouvez utiliser la **redéfinir**, **incluent**, et **importer** éléments lorsque vos schémas gagnent en taille et complexes, ou lorsque les schémas représentant vos différents types de messages d’instance comportent plusieurs portions en commun. Il peut être utile de combiner des schémas plus petits en des schémas qui définiront la structure finale des messages d'instance que vous prévoyez d'échanger avec des partenaires commerciaux. Vous pouvez publier ces schémas sous la forme de services WCF à l'aide de l'Assistant Publication de services WCF BizTalk.  
  
 Vous devez utiliser l'Assistant Consommation de service WCF BizTalk pour créer les artefacts de BizTalk nécessaires à l'utilisation des services WCF à partir d'un projet BizTalk. Si vous voulez utiliser les services WCF à partir d'une application .NET, vous devez utiliser l'outil Service Model Metadata Utility (Svcutil.exe) pour créer la classe proxy pour les services WCF. Pour plus d’informations sur la façon d’utiliser des schémas qui référencent d’autres schémas, consultez [schémas qui utilisent d’autres schémas](../core/schemas-that-use-other-schemas.md) et [comment créer des schémas qui utilisent d’autres schémas](../core/how-to-create-schemas-that-use-other-schemas.md). Pour plus d’informations sur Svcutil.exe, consultez « Service Model Metadata utilitaire Tool (Svcutil.exe) » à [http://go.microsoft.com/fwlink/?LinkID=74696](http://go.microsoft.com/fwlink/?LinkID=74696).  
  
 Le tableau suivant montre les restrictions et considérations à prendre en compte lors de l'utilisation de services WCF publiés à l'aide de schémas utilisant d'autres schémas.  
  
|Élément de schéma XML|Utilisation de services WCF publiés à l'aide de l'Assistant Publication de services WCF BizTalk|Utilisation de services WCF hébergés par des applications .NET|  
|------------------------|-------------------------------------------------------------------------------------|--------------------------------------------------------|  
|\<importation\>|Prise en charge par l'Assistant Consommation de service WCF BizTalk et Svcutil.exe|Prise en charge par l'Assistant Consommation de service WCF BizTalk et Svcutil.exe|  
|\<inclure\>|Prise en charge avec l’Assistant consommation de Service WCF de BizTalk et Svcutil.exe **Remarque :** Svcutil.exe peut générer un message d’avertissement lors de la création de la classe proxy.|Prise en charge avec l’Assistant consommation de Service WCF de BizTalk et Svcutil.exe **Remarque :** Svcutil.exe peut générer un message d’avertissement lors de la création de la classe proxy.|  
|\<redéfinir\>|-Prise en charge avec l’Assistant consommation de Service WCF BizTalk<br />-Limitée de prise en charge par Svcutil.exe **Remarque :** Svcutil.exe connaît la même restriction pour le **redéfinir** a de l’élément en tant que XSD.exe.|Prise en charge avec l’Assistant consommation de Service WCF de BizTalk et Svcutil.exe **Remarque :** Svcutil.exe peut générer un message d’avertissement lors de la création de la classe proxy.|  
  
> [!NOTE]
>  SvcUtil.exe peut générer un message d’avertissement lors de la création de la classe proxy sur le service WCF BizTalk publié avec les schémas à l’aide de la **incluent** et **redéfinir** éléments. Par exemple, « L'élément global a déjà été déclaré ».  
  
## <a name="ensure-that-an-in-process-wcf-receive-location-is-not-disabled-after-you-change-the-computer-name-part-in-its-service-endpoint-address"></a>Vérification qu'un emplacement de réception WCF in-process n'est pas désactivé après la modification du nom de l'ordinateur indiqué dans l'adresse de point de terminaison de son service  
 Si vous modifiez la partie nom d’ordinateur dans le **adresse (URI)** emplacement de réception de zone de texte d’un processus en cours d’exécution de WCF, nous vous recommandons d’utiliser la console Administration de BizTalk pour vérifier si l’emplacement de réception est en cours d’exécution. Par exemple, si vous modifiez une adresse de point de terminaison de service à l’aide de WCF-NetTcp adaptateur de réception, **net.tcp://\<***nom de votre ordinateur***\>/samplepath**, **net.tcp://localhost/samplepath**, l’emplacement de réception peut être désactivé avec un **Service.InvalidOperationException**. Si vous modifiez uniquement le nom de l'ordinateur indiqué dans l'adresse de point de terminaison de service sans changer le chemin d'accès, assurez-vous que l'emplacement de réception n'est pas désactivé et activez-le si nécessaire.  
  
## <a name="set-the-appropriate-msdtc-security-configuration-options-on-client-computers-communicating-with-remote-wcf-receive-locations-through-a-transaction-protocol"></a>Définition des options de configuration de la sécurité MSDTC appropriées sur les ordinateurs clients communiquant avec des emplacements de réception WCF distants via un protocole de transaction  
 Adaptateurs de réception WCF-NetTcp, WCF-WSHttp et WCF-NetNamedPipe peut participer au processus de coordination transactionnelle clients WCF gèrent à la **WS-AtomicTransaction** et **OleTransaction**protocoles de transaction. Les messages peuvent être transmis aux emplacements de réception de destination et supprimés de la base de données MessageBox, dans un contexte transactionnel, à l'aide des protocoles de transaction.  
  
 Pour communiquer à distance les emplacements de réception WCF à l’aide de protocoles de transaction, vous devez correctement configurer MSDTC **Configuration de la sécurité** options sur les ordinateurs clients WCF. Le tableau suivant répertorie les valeurs requises pour les options qui sont disponibles dans le service MSDTC **Configuration de la sécurité** boîte de dialogue :  
  
|Option de configuration|Valeur par défaut|Valeur recommandée|  
|--------------------------|-------------------|-----------------------|  
|Accès DTC réseau|Désactivé|Activé|  
|Autoriser les transactions sortantes|Désactivé|Activé|  
|Authentification mutuelle requise|Activé|Activé si l’instance distante correspondante recevez emplacements exécutent Windows Server 2003 SP1 ou SP2 et sont configurés avec **authentification mutuelle requise**.|  
|Autorisation de l'appelant entrant requise|Désactivé|Activé si MSDTC est exécuté sur un cluster.|  
  
 Après avoir appliqué ces modifications, vous devez redémarrer le service MSDTC.  
  
 Pour accéder à la ressource MSDTC **Configuration de la sécurité** boîte de dialogue zone, procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**et le type **dcomcnfg** pour lancer le **Services de composants** console de gestion.  
  
2.  Développez **Services de composants**, développez **ordinateurs**, avec le bouton droit **poste**, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés Poste de travail** boîte de dialogue, cliquez sur le **MSDTC** onglet, puis cliquez sur **Configuration de la sécurité** pour afficher les **Configuration de la sécurité**  boîte de dialogue.  
  
## <a name="explanation-of-the-soap-wrapper-when-using-the-biztalk-wcf-service-publishing-wizard"></a>Wrapper SOAP avec l'Assistant Publication de services WCF BizTalk  
 Lorsqu'une orchestration est exposée en tant que service [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] à l'aide de l'Assistant Publication de services [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)], un wrapper est généré. Ce wrapper utilise le nom de méthode du port, présent dans le message XML, auquel le message est envoyé. Ce wrapper est la valeur par défaut pour les enveloppes SOAP de Microsoft. Il permet à [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] de wrapper le message SOAP à parties multiples dans un seul message WCF à transmettre au point de terminaison par l'adaptateur.  
  
 Il est recommandé que l'expéditeur utilise un wrapper et que le destinataire l'attende ou que l'expéditeur n'utilise pas de wrapper et que le destinataire attende un message [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] brut. L'absence d'accord préalable sur l'utilisation ou non d'un wrapper peut causer des problèmes d'incompatibilité entre ce qui est envoyé et ce qui est reçu.