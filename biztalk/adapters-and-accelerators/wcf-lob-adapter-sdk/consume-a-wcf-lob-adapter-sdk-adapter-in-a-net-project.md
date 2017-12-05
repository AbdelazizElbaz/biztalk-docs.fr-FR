---
title: Utiliser un adaptateur WCF LOB Adapter SDK dans un projet .NET | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6934b96d-5704-4f3c-b53f-4e36e352a338
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 622c6ad687e681591071d472e2ff8a9e8c515f95
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="consume-a-wcf-lob-adapter-sdk-adapter-in-a-net-project"></a>Utiliser un adaptateur WCF LOB Adapter SDK dans un projet .NET
Pour utiliser un adaptateur créé à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous devez ajouter une référence de service au projet. Vous pouvez faire cela :  
  
-   À l’aide de la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], qui est installé dans le cadre de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].  
  
-   À l’aide de svcutil.exe (le service Model Metadata), qui est installé en tant que partie du Kit de développement Windows.  
  
## <a name="add-a-service-reference-using-the-add-adapter-service-reference-plug-in"></a>Ajouter une référence de Service à l’aide de l’ajouter adaptateur Service référence un plug-in  
 Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] peut être utilisé pour parcourir et rechercher des métadonnées et pour générer des classes de proxy .NET CLR à l’aide des opérations sélectionnées et les types.  
  
 
1.  Ouvrez votre application .NET dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
2.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], avec le bouton droit le **projet** menu, puis sur **ajouter une référence de Service de carte**.  
  
    > [!NOTE]
    >  Cette option n’apparaît pas pour [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projets.  
  
3.  Dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] écran, à partir de la **sélectionner une liaison** liste déroulante, sélectionnez une liaison de la carte.  
  
4.  Pour configurer l’URI de connexion pour la liaison de la carte sélectionnée et fournir toutes les informations d’identification, les propriétés d’URI et les propriétés de liaison, cliquez sur **configurer**. La configuration requise réelle varie en fonction de la liaison de la carte sélectionnée.  
  
5.  Lorsque vous avez configuré l’URI, cliquez sur **OK**.  
  
6.  Cliquez sur **Se connecter**. Si l’URI de connexion est valide et les informations d’identification de client (le cas échéant) sont acceptées, la **catégorie** volet doit être rempli avec les catégories et les opérations fournies par l’adaptateur.  
  
7.  Si l’adaptateur prend en charge la recherche, le champ de recherche sera actif. Sinon, vous pouvez filtrer par type de contrat, Explorer les types et les opérations en cliquant sur les nœuds dans le **catégorie** volet.  
  
8.  Pour les options de génération de proxy avancés, cliquez sur **avancé**. Parmi les options, citons :  
  
    |Option|Option de l’équivalent de svcutil.exe| Description|  
    |------------|-----------------------------------|-----------------|  
    |**Générer des méthodes asynchrones**|/Async|Génère les signatures de méthode synchrones et asynchrones.<br /><br /> Par défaut (si non sélectionnée) : génère des signatures de méthode synchrones uniquement.|  
    |**Générer des contrats de message**|/messageContract|Génère des types de contrat de message.|  
    |**Vérifiez les types internes**|/ interne|Génère des classes marquées comme internes.<br /><br /> Par défaut (si non sélectionnée) : générer des classes publiques.|  
    |**Activer la liaison de données**|/enableDataBinding|Implémente le System.ComponentModel.INotifyPropertyChanged interface sur tous les types de contrat de données pour activer la liaison de données.|  
    |**Importer des types de données non-comme IXmlSerializable**|/importXmlTypes|Configure le sérialiseur de contrat de données pour importer des types de contrat de données non - en tant que types IXmlSerializable.|  
    |**Générer l’interface de canal**||Génère l’interface de canal.|  
    |**Marquer des classes sérialisables**||S’il faut générer les types de données avec un sérialiseur sélectionne.|  
    |**Ne pas générer de app.config**|/noconfig ignorée|Ne génère pas de fichier de configuration d’application.|  
    |**Sérialiseur**<br /><br /> **Automatique**|/Serializer:auto|Sélectionne automatiquement le sérialiseur pour la sérialisation et désérialisation.|  
    |**Sérialiseur**<br /><br /> **Sérialiseur DataContract**|/Serializer:DataContractSerializer|Génère des types de données qui utilisent le sérialiseur de contrat de données pour la sérialisation et désérialisation|  
    |**Sérialiseur**<br /><br /> **XmlSerializer**|/ Serializer : XmlSerializer|Génère des types de données qui utilisent le XmlSerializer pour la sérialisation et la désérialisation.|  
  
9. Pour générer les artefacts de proxy, cliquez sur **OK**. Le nombre d’artefacts varie en fonction du type de contrat.  
  
    |Type de contrat|Artefact| Description||  
    |-------------------|--------------|-----------------|-|  
    |Sortant|Proxy WCF du CLR|Contient l’implémentation de contrat et le service.||  
    |Sortant||App.config|Contient le \<point de terminaison\> et \<liaisons\> éléments pour \<système. ServiceModel\>\<client\>.|  
    |Trafic entrant|Interface de service WCF du CLR|Contient le contrat.||  
    |Trafic entrant||Implémentation de service CLR WCF|Implémentation d’un stub qui dérive du contrat.|  
    |Trafic entrant||App.config|Contient le \<point de terminaison\>, \<liaisons\> et \<comportements\> éléments pour \<système. ServiceModel\>\<service\>.|  
  
10. Vous pouvez maintenant utiliser le proxy dans votre application.  
  
## <a name="adding-a-service-reference-by-using-svcutilexe"></a>Ajout d’une référence de Service à l’aide de svcutil.exe  
 SvcUtil.exe est un utilitaire de ligne de commande qui peut être utilisé pour récupérer les métadonnées et générer des classes proxy .NET CLR, ce qui peuvent ensuite être ajoutés à un [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] projet. Pour plus d’informations sur svcutil.exe, consultez [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx). 
  
 Pour générer une classe proxy à partir d’un adaptateur hébergé dans IIS  
  
1.  À l’invite de commandes, entrez **svcutil.exe « http://localhost/adapter/AdapterService.svc?wsdl » /config:app.config**. Remplacez le chemin d’accès HTTP avec le chemin d’accès approprié pour votre adaptateur hébergé. Cette opération crée un fichier .cs qui contient le proxy de CLR .NET et output.config qui contient le \<liaisons\> et le client \<point de terminaison\> pour \<system.serviceModel\>.  
  
    > [!NOTE]
    >  Si votre carte contient de nombreuses opérations, vous pouvez limiter les opérations retournées à l’aide d’une chaîne de requête de ' op = » suivi du nom de l’opération qui vous intéressent. Par exemple : `svcutil.exe “http://localhost/adapter/AdapterService.svc?wsdl&op=Echo/EchoString&op=Echo/EchoArray”` génère le code proxy pour seulement les opérations EchoString et EchoArray.  
  
2.  Ouvrez votre projet dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
    1.  Dans **l’Explorateur de solutions**, cliquez sur le projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Dans le **ajouter un élément existant** boîte de dialogue, sélectionnez les fichiers .cs et app.config créés précédemment.  Cliquez sur **Ajouter**.  
  
    2.  Dans **l’Explorateur de solutions**, avec le bouton droit **références**, puis cliquez sur **ajouter une référence**. Sur le **.NET** onglet, sélectionnez **System.ServiceModel**, puis cliquez sur **OK**. Vous pouvez maintenant utiliser le proxy dans votre application.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 1 : Développer l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)   
 [Utiliser un adaptateur créé à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/consume-an-adapter-created-using-the-wcf-lob-adapter-sdk.md)