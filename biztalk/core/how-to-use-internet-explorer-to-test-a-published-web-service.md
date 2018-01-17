---
title: Tester le service web de BizTalk | Documents Microsoft
description: "Configurer les emplacements de réception et web.config pour tester le service web BizTalk dans un navigateur web"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4dc2171d-4abe-43db-b4bc-e484048c6430
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48a35373735102bd75d1c388da29b06d4392ba18
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="test-a-biztalk-web-service"></a>Tester un Service Web BizTalk

## <a name="overview"></a>Vue d'ensemble
Vous pouvez tester votre service Web publié sans écrire d'application cliente Web. Vous pouvez utiliser un navigateur Web, tel qu'Internet Explorer, pour tester votre service Web publié. Bien que vous puissiez accéder à tout service Web publié à l'aide d'un navigateur Web, vous pouvez uniquement tester les services Web avec des méthodes Web contenant des paramètres de type simple. Pour tester votre méthode Web dans un navigateur Web, vos parties de message pour les messages de demande et de réponse qui sont utilisés dans le port de réception peuvent uniquement être un type simple, tel que **System.String** ou **System.Int32**. Si une partie de message utilise un schéma comme type de message, vous ne pouvez pas tester la méthode Web à l'aide d'un navigateur.  
  
 Si vous voulez tester vos services Web publiés à l'aide de HTTP-GET ou HTTP-POST, vous devez configurer votre emplacement de réception BizTalk pour l'adaptateur SOAP et modifier le fichier Web.config pour votre service Web publié.  
  
 **Modifier les emplacements de réception**  
  
 Lorsque l'adaptateur SOAP configure des emplacements de réception, il définit normalement l'URI de l'emplacement de réception en donnant les noms du répertoire virtuel et du fichier .asmx du service Web :  
  
```  
/PurchaseOrder/POOrchestration.asmx  
```  
  
 Cela permet à l'adaptateur SOAP de recevoir des demandes de service Web à l'aide du protocole HTTP-SOAP. Pour configurer l'emplacement de réception pour utiliser le protocole HTTP-GET ou HTTP-POST, vous devez ajouter le nom de la méthode à l'URI :  
  
```  
/PurchaseOrder/POOrchestration.asmx/Operation_1  
```  
  
 Le nom de la méthode est identique à celui de l'opération de port dans l'orchestration.  
  
 **Modification du fichier Web.config**  
  
 Par défaut, l'Assistant configure les services Web pour utiliser le protocole HTTP-SOAP. HTTP-GET et HTTP-POST sont explicitement désactivés. Pour tester un service Web à l'aide d'un navigateur Web, vous devez activer HTTP-GET.  
  
## <a name="update-the-webconfig"></a>Mettre à jour le fichier Web.config
  
1.  Ouvrez le fichier Web.config pour le service Web publié.  
  
    > [!NOTE]
    >  Vous pouvez trouver le fichier Web.config dans le répertoire que vous avez configuré pour la racine virtuelle IIS contenant le service Web.  
  
2.  Rechercher les \<protocoles\> section :  
  
    ```  
    <webServices>  
       <protocols>  
         <remove name="HttpPost" />  
         <remove name="HttpGet" />  
         <remove name="HttpPostLocalhost" />  
       </protocols>  
  
    </webServices>  
    ```  
  
3.  Pour tester HTTP-GET, HTTP-POST ou HTTP-POST depuis l’ordinateur local, supprimez la ligne correspondante à partir de la \<protocoles\> section.  
  
 Pour plus d’informations sur les options de configuration, consultez [Options de Configuration pour les Services Web XML créés à l’aide d’ASP.NET](https://msdn.microsoft.com/library/b2c0ew36.aspx). 
  
#### <a name="access-a-web-service-with-internet-explorer"></a>Accéder à un service Web avec Internet Explorer  
  
-   Dans Internet Explorer, dans le **adresse** zone, tapez l’URL du service Web en utilisant le format **http://*nom_serveur*/*apppath* / *webservicename*.asmx**.  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |***servername***|Nom du serveur sur lequel vous avez déployé le service Web XML.|  
    |***Apppath***|Nom du répertoire virtuel et chemin d'accès à l'application Web|  
    |***webservicename.asmx***|Nom du fichier .asmx de service Web XML|  
  
 La description du service Web vous montre toutes les méthodes de service Web prises en charge par le service Web particulier. La page de description du service Web contient des liens pour chaque méthode Web disponible et la description du service Web.  
  
#### <a name="test-a-web-service-with-internet-explorer-using-http-get"></a>Tester un service Web avec Internet Explorer à l’aide de HTTP-GET  
  
1.  Après avoir accédé à la page de description du service Web, cliquez sur l'une des méthodes Web répertoriées dans cette page.  
  
2.  Les paramètres nécessaires pour la méthode Web, puis tapez **Invoke**.  
  
3.  Le serveur renvoie une réponse XML dans le navigateur. Si le type de données renvoyées pour le service Web est un nombre à virgule flottante double précision, le résultat doit ressembler à ce qui suit :  
  
    ```  
    <?xml version="1.0" ?>  
    <double>74.5</double>  
    ```  
  
#### <a name="test-a-web-service-with-internet-explorer-using-http-get-alternate-method"></a>Tester un service Web avec Internet Explorer à l’aide de HTTP-GET (autre méthode)  
  
1.  Dans Internet Explorer, dans le **adresse** zone, tapez l’URL du service Web en utilisant le format ***http://servername/vdir/webservicename.asmx/Methodname?parameter=value***.  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |***servername***|Nom du serveur sur lequel vous avez déployé le service Web XML.|  
    |***Apppath***|Nom du répertoire virtuel et chemin d'accès à l'application Web|  
    |***webservicename.asmx***|Nom du fichier .asmx de service Web XML|  
    |***MethodName***|Nom d'une méthode publique que le service Web XML expose. Si vous n'indiquez rien, la page de description du service Web XML apparaît, répertoriant chaque méthode publique disponible dans le fichier .asmx. (Facultatif)|  
    |***parameter***|Nom du paramètre approprié et valeur des paramètres requis par votre méthode. Si vous n'indiquez rien, la page de description du service Web XML apparaît, répertoriant chaque méthode publique disponible dans le fichier .asmx. (Facultatif)|  
  
    > [!NOTE]
    >  Dans cette syntaxe, le nom de la méthode de service Web XML est sensible à la casse, contrairement aux noms du serveur, du projet et du service Web XML.  
  
2.  Appuyez sur Entrée. Le navigateur Web affiche une réponse XML à partir du serveur.  
  
    > [!NOTE]
    >  Vous pouvez également utiliser HTTP-POST pour appeler le service Web. Pour plus d’informations et des exemples d’appel de services Web XML à partir d’un navigateur Web, consultez [Access XML Web Services à partir d’un navigateur](https://msdn.microsoft.com/library/45fez2a8.aspx).  
  
## <a name="see-also"></a>Voir aussi  
 [Test des services web publiés](../core/testing-published-web-services.md)