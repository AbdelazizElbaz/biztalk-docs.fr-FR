---
title: "Problèmes connus avec WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2cda4248-2efa-4e3d-a5ce-9a57728c51e1
caps.latest.revision: "35"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d718450dfd4db1fd6d695c1a3ecc21f9f1fd8deb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="known-issues-with-the-wcf-lob-adapter-sdk"></a>Problèmes connus avec WCF LOB Adapter SDK
Cette rubrique décrit les problèmes connus associés à le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. Il propose également des solutions pour certains de ces problèmes.  
  
## <a name="unable-to-change-sdk-features-using-add-or-remove-programs"></a>Impossible de modifier les fonctionnalités de kit de développement logiciel à l’aide d’Ajout / Suppression de programmes
 **Problème**: à l’aide de **Ajout / Suppression de programmes** dans le panneau de configuration ne parvient pas à modifier les fonctionnalités pour le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sur un ordinateur exécutant Windows Vista.  
  
 **Résolution**: au lieu d’utiliser **Ajout / Suppression de programmes** pour modifier votre installation, réexécutez le programme Setup.exe.  
  
## <a name="base-runtime"></a>Runtime de base  
  
### <a name="applications-using-transactions-in-asynchronous-proxy-must-explicitly-call-proxyopen"></a>Applications à l’aide de Transactions dans le Proxy asynchrone doivent appeler explicitement Proxy.Open  
 **Problème**: les Applications qui utilisent des transactions avec une carte dans un proxy asynchrone doivent appeler explicitement de proxy. Ouvert pour les transactions de flux.  
  
 **Résolution**: cela une fois que le proxy généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] dans le programme client, comme indiqué :  
  
```  
EchoAdapterClient echoAdapterProxy = new EchoAdapterClient("mEchoConfiguration");  
echoAdapterProxy.Open();  
...  
```  
  
### <a name="iduplexchannel-shape-not-supported"></a>Forme de IDuplexChannel pas pris en charge  
 **Problème**: IDuplexChannel la forme du canal n’est pas pris en charge dans cette version.  
  
 **Résolution**: le modèle de canal WCF permet de créer une liaison WCF personnalisée qui prend en charge des canaux duplex.  
  
### <a name="request-schema-generated-with-or-without-in-or-out-parameters"></a>Schéma de requête généré avec ou sans ou les paramètres de sortie  
 **Problème**: dans le **ExportInputXmlSchema** méthode de la classe **OperationMetadata**, le schéma de demande est toujours généré, même si elle ne peut pas contenir un dans ou sur les paramètres de sortie.  
  
### <a name="providing-multiple-operation-namespaces"></a>En fournissant plusieurs espaces de noms opération  
 **Problème**: si le développeur d’adaptateurs fournit plusieurs espaces de noms opération pour le groupe d’une seule opération, le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] génère un WSDL non valide. L’entrée générée et la partie de message de sortie pour chaque opération ne seront pas liés à la référence de schéma approprié.  
  
 **Résolution**: Assurez-vous que chaque OperationMetadata.OperationGroup est mappée à un seul OperationMetadata.OperationNamespace.  
  
### <a name="overloaded-operations-not-supported"></a>Opérations surchargées ne pas pris en charge  
 **Problème**: dans cette version, le composant de générateur de contrat dynamique (générateur WSDL) du Kit de développement ne prend pas en charge les opérations surchargées, autrement dit, les opérations avec le même nom signature mais différente.  
  
### <a name="fault-contract-not-supported"></a>Contrat d’erreur non pris en charge.  
 **Problème**: dans cette version, le composant de générateur de contrat dynamique (générateur WSDL) du SDK ne prend pas en charge les métadonnées de contrat d’erreur.  
  
### <a name="failure-when-receiving-messages"></a>Échec lors de la réception des Messages  
 **Problème**: lors de la réception, il est possible de l’adaptateur échouent lors du traitement de certains messages si le **délai d’attente de réception** liaison de la propriété est définie sur une valeur faible. L’erreur retournée sera spécifique à votre carte.  
  
 **Solution de contournement**: définir le **délai d’attente de réception** liaison de propriété à une valeur élevée, par exemple 23:59:59, qui est la valeur maximale.  
  
### <a name="adapter-stalls-during-message-processing"></a>Blocages de carte lors du traitement du Message  
 **Problème**: s’il existe un grand nombre de demandes à l’adaptateur, le traitement des éléments de travail peut-être apparaître à la place.  
  
 Lorsque vous ouvrez une nouvelle connexion, l’adaptateur file d’attente un élément de travail qui est traité par le pool de threads .NET. Une fois qu’une connexion est ouverte, plus les éléments de travail sont en attente pour traiter chaque message. Si le pool de threads est épuisé, un interblocage peut se produire dans laquelle les demandes d’ouverture de nouvelles connexions sont bloque les demandes pour traiter les messages.  
  
 **Résolution**: finit par les demandes va expirer et par le traitement va continuer, mais la résolution recommandée consiste soit réduire le nombre de messages à traiter ou augmenter le nombre de threads dans le threadpool.  
  
 Pour augmenter le nombre de threads, modifiez la valeur de [ProcessModelSection.MaxWorkerThreads propriété](https://msdn.microsoft.com/library/system.web.configuration.processmodelsection.maxworkerthreads.aspx).  
  
## <a name="design-time-proxy-and-schema-generation-tools"></a>Au moment du design Proxy et les outils de génération de schéma  
  
### <a name="limitations-with-select-contract-type"></a>Limitations de Type de contrat Select  
 **Problème**: le filtrage de « type de contrat Select » est appliqué à l’arborescence de la catégorie et la liste des opérations disponibles. Si le consommateur de l’adaptateur sélectionne un nœud de catégorie contenant des opérations entrantes et sortantes, tous les feront partie de WSDL et du proxy généré, quel que soit le filtrage « type de contrat Select ».  
  
 **Résolution**: sélectionner des opérations individuelles, au lieu de sélectionner l’ensemble de la catégorie.  
  
### <a name="error-with-add-adapter-service-reference-visual-studio-plug-in"></a>Erreur avec ajouter l’adaptateur Service Reference Visual Studio plug-in  
 **Problème**: projet dans un BizTalk dans Visual Studio, si un proxy a déjà été généré à l’aide de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], génération d’un autre proxy à partir de la même carte génère cette erreur : « l’espace de noms '\<espace de noms global\>' contient déjà une définition pour '{nom de contrat}' lorsque la compilation du projet. »  
  
 Cette version n’autorise pas la modification du proxy.  
  
 **Résolution**: supprimer les fichiers superflus proxy dans le projet BizTalk. Si des opérations supplémentaires doivent être incluses dans le proxy généré, supprimez le fichier de proxy et utiliser le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour rechercher ou parcourir les métadonnées et régénérer le proxy.  
  
### <a name="error-with-consume-adapter-service-biztalk-project-add-in"></a>Erreur avec Consume Adapter Service BizTalk Project Add-In  
 **Problème**: comme dans le problème précédent, dans BizTalk de projet dans Visual Studio, si les types common existent dans les schémas générés à partir de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], le projet BizTalk ne parvient pas à compiler.  
  
 **Résolution**: supprimer les fichiers de schéma XML superflus dans le projet BizTalk, utilisez la référence Consume Adapter Service pour rechercher ou parcourir les métadonnées requises et régénérer les nouveaux fichiers de schéma XML.  
  
### <a name="error-with-rootnode-typename-in-biztalk-projects"></a>Erreur avec RootNode TypeName dans les projets BizTalk  
 **Problème**: projet dans un BizTalk dans Visual Studio, si les schémas générés à partir de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] contiennent des caractères non valides ou des mots réservés pour le **RootNode TypeName** propriété, l’erreur suivante se produit à moment de la compilation : « nœud \<référence de nœud\> -spécifiez un nom de type .NET valide pour ce nœud racine.  Le nom de type .NET actuel de ce nœud racine n’est pas valide (elle est un mot clé BizTalk réservé ou un identificateur c# non valide).  
  
 **Résolution**: sélectionnez le nœud racine référencé dans l’erreur et, dans Propriétés, supprimez tous les caractères non autorisés ou mots réservés à partir de la **RootNode TypeName** propriété.  
  
### <a name="metadata-generation-tool-limitations"></a>Limitations d’outil de génération de métadonnées  
 **Problème**: si le développeur d’adaptateurs fournit une structure de schéma XML dans un OperationMetadata et/ou de TypeMetadata de classe dérivée, et le schéma XML contient des constructions qui sont ignorées ou interdites par DataContractSerializer, les métadonnées outil de génération revienne à l’aide de XmlSerializer pour la sérialisation.  
  
 **Résolution**: supprimez les constructions interdites dans le schéma, ou utilisez le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] modèle d’objet de métadonnées pour générer les définitions de schéma XML qui sont conformes aux DataContractSerializer.  
  
### <a name="binding-name-property-does-not-take-effect"></a>Propriété de nom de liaison ne prend pas effet  
 **Problème**: modification de la propriété de nom de liaison sur le **général des propriétés de liaison** onglet de la **ajouter une référence de Service de carte** boîte de dialogue ne prendront pas effet.  
  
 **Résolution**: utilisez le AdapterBinding dérivés de classe pour modifier le nom comme suit :  
  
```  
[Browsable(false)]  
public new virtual string Name  
{  
     set  
     {  
          base.Name = value;  
     }  
     get  
     {  
          return base.Name;  
     }  
}  
```  
  
### <a name="timeout-when-retrieving-metadata"></a>Délai d’attente lors de la récupération des métadonnées  
 **Problème**: si l’adaptateur contient de nombreuses opérations, vous pouvez rencontrer un délai d’attente lors de la récupération de métadonnées à l’aide des outils tels que le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], WCF Assistant développement d’adaptateurs, ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] si vous tentez de récupérer de nombreuses opérations au niveau fois.  
  
 **Résolution**: réduire le nombre d’opérations sélectionnées.  
  
### <a name="avoid-generating-schemas-which-reference-an-external-import"></a>Éviter de générer des schémas qui font référence à une importation externe  
 **Problème**: vous devez éviter de générer des schémas qui contiennent une ou plusieurs références aux importations externes. Si cette opération est effectuée, les liens externes ne seront pas suivis.  
  
## <a name="setup"></a>Programme d'installation  
  
### <a name="setup-halts-while-checking-disk-space"></a>Le programme d’installation s’arrête lors de la vérification de l’espace disque  
 **Problème**: lors de l’installation [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], vous pouvez recevoir une boîte de dialogue indiquant que le programme d’installation vérifie l’espace disque disponible et que le programme d’installation ne continuera pas.  
  
 **Résolution**: quand ce problème se produit, vous pouvez contourner ce problème en effectuant une installation silencieuse de [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] à une invite de commandes. Exemple :  
  
```  
Msiexec.exe /package AdapterFramework.msi /qr  
```  
  
### <a name="biztalk-server-developer-tools-required"></a>Outils de développement BizTalk Server requis  
 **Problème**: lorsque le système cible a Visual Studio et Microsoft BizTalk Server sans les outils de développement, le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] le programme d’installation échoue. Il s’agit, car elle requiert des outils de développement BizTalk Server soit présent sur l’ordinateur pour installer le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
 **Résolution**: Assurez-vous que l’ordinateur cible dispose de BizTalk Server est installé avec les outils de développement avant d’installer le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].  
  
### <a name="corrupt-biztalk-server-installation-causes-sdk-to-fail"></a>Endommagé BizTalk Server Installation provoque SDK Échec  
 **Problème**: une installation endommagée de BizTalk Server peut entraîner l’installation du Kit de développement logiciel échoue avec l’erreur suivante : « exception DirectoryNotFound. »  
  
 **Résolution**: désinstaller et réinstaller BizTalk Server.  
  
 
## <a name="see-also"></a>Voir aussi  
 [Prise en main de BizTalk Server](../../core/getting-started-with-biztalk-server.md)