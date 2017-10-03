---
title: "Étape 2 : Configurer un Port d’envoi WCF-WebHttp bidirectionnel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bcab296-7921-4df4-abcc-eea78cc827e8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f355275f9480cfa13f3a15bcc6522fbe7ec83b8c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-a-two-way-wcf-webhttp-send-port"></a>Étape 2 : Configurer un Port d’envoi WCF-WebHttp bidirectionnel
Dans cette étape, vous configurez un texte bidirectionnel **WCF-WebHttp** port d’envoi pour appeler l’URL de ressource REST pour récupérer des retards dans les planifications des transporteurs aériens américains.  
  
### <a name="to-configure-wcf-webhttp-send-port"></a>Pour configurer le port d’envoi WCF-WebHttp  
  
1.  À partir de la Console Administration de BizTalk Server, sous la **BizTalk Application 1** nœud, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **statique Port d’envoi de sollicitation-réponse**.  
  
2.  Sous l'onglet **Général** , effectuez les paramétrages suivants :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **SendPortRESTAzureMarketPlace**.|  
    |**Type**|Sélectionnez **WCF-WebHttp**.|  
    |**Gestionnaire d’envoi**|Sélectionnez **BizTalkServerApplication**.|  
    |**Pipeline d’envoi**|Sélectionnez **PassThruTransmit**.|  
    |**Pipeline de réception**|Sélectionnez **PassThruReceive**.|  
  
     Cliquez sur **configurer**.  
  
3.  À partir de la **propriétés du Transport WCF-WebHttp** boîte de dialogue zone, procédez comme suit :  
  
    1.  Sur le **général** onglet, pour **adresse (URI)**, entrez `https://api.datamarket.azure.com/oakleaf/US_Air_Carrier_Flight_Delays_Incr/`.  
  
    2.  Sous l’onglet Général, pour **méthode HTTP et mappage d’URL**, entrez les informations suivantes :  
  
        ```  
        <BtsHttpUrlMapping>  
        <Operation Method="GET" Url="/On_Time_Performance" />  
        </BtsHttpUrlMapping>  
  
        ```  
  
         Ici, **obtenir** est le verbe HTTP et **On_Time_Performance** est ajouté à l’URI de base pour construire une URL de ressource unique pour extraire les retards de vol.  
         
         > [!TIP] 
         > Dans le champ URL, tous les caractères XML spéciaux doivent être « échappés ». Cela garantit que les caractères XML spéciaux sont traitées et conservées par le port. Par exemple, le `&` caractères spéciaux doivent être échappés en tant que `&amp;`. 
           >
           >De :`Url=”/Customer?{ID}& group=Location”`
           >
           >
           >À :`Url=”/Customer?{ID}&amp;group=Location”`
  
    3.  Sur le **liaisons** onglet, pour le **taille de Message maximale reçus** , sélectionnez une valeur suffisamment élevée. car généralement, le message de réponse contenant les informations sur le vol est relativement volumineux et risque de dépasser la taille des messages spécifiée par défaut.  
  
    4.  Sur le **sécurité** onglet, procédez comme suit :  
  
        1.  Pour le **mode de sécurité**, sélectionnez **Transport**.  
  
        2.  Pour **type d’informations d’identification du client du Transport**, sélectionnez **base**.  
  
        3.  Sous le **informations d’identification utilisateur** , cliquez sur **modifier**. Dans le **informations d’identification Client** boîte de dialogue, sélectionnez **ne pas utiliser l’authentification unique sur**et entrez le nom d’utilisateur et un mot de passe que vous avez récupéré à partir de la **mon compte** onglet une fois que vous avez connecté à [Windows Azure Marketplace](http://go.microsoft.com/fwlink/p/?LinkId=257913). Les informations d’identification sont répertoriées par rapport à la **ID de client** (nom d’utilisateur) et **clé de compte primaire** les étiquettes (mot de passe).  
  
        4.  Cliquez sur **OK**.  
  
    5.  Sur le **Messages** onglet, pour **supprimer le corps en fonction de verbes**, spécifiez le verbe pour lequel vous souhaitez supprimer la charge du message de demande. Pour ce didacticiel, spécifiez `GET`. Voici pourquoi : un appel de méthode GET au point de terminaison REST des retards de vol transporteurs aériens américains ne nécessite pas une charge utile de message ; l’URL de ressource REST suffit récupérer les informations. Toutefois, pour déclencher le **WCF-WebHttp** port d’envoi qui effectue l’appel REST, vous déposez un message factice comportant un corps de message. Le port d’envoi ne doit pas envoyer ce message factice au point de terminaison REST, car, comme expliqué plus haut, le point de terminaison n’attend pas de charge de message. Par conséquent, avant d’appeler le point de terminaison REST, l’adaptateur supprime la charge utile de message du message factice uniquement pour les verbes que vous spécifiez dans le **supprimer le corps en fonction de verbes** zone de texte.  
  
    6.  Cliquez sur **OK** jusqu'à ce que vous êtes dans la boîte de dialogue Propriétés de Port d’envoi. Dans le volet gauche, cliquez sur **filtres**et spécifiez le filtre à utiliser tous les messages reçus via la réception du port que vous avez créé dans [étape 1 : configurer un emplacement de réception du fichier](../core/step-1-configure-a-file-receive-location.md).  
  
        |||  
        |-|-|  
        |**Propriété**|La valeur **BTS. ReceivePortName**|  
        |**Opérateur**|La valeur**==**|  
        |**Valeur**|La valeur`ReceivePortRestAzureMarketPlace`|  
  
    7.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel de 5 : Appeler une Interface REST à l’aide de BizTalk Server](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)