---
title: Glossary8 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d271fe0-1b54-4a83-87e6-20aa1c37df97
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a89d9aee3652f0e76714184d4f3a9a18ad610173
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="glossary"></a>Glossaire
Cette rubrique définit les termes clés utilisés dans ce guide.  
  
## <a name="glossary"></a>Glossaire  
  
|Terme|Définition|  
|----------|----------------|  
|**contrôleur d’interruptions programmable avancé APIC)**|Un contrôleur qui reçoit des interruptions à partir de différentes sources et les envoie à un noyau de processeur pour la gestion. Dans un système multiprocesseur, qui peut être un ordinateur virtuel ou un ordinateur physique, APIC envoie et recevoir des messages d’interruption INTERPROCESSEUR vers et depuis d’autres processeurs logiques sur le bus système. Pour plus d’informations sur le contrôleur d’interruptions programmable avancé, consultez le chapitre 8 du [3 a Manual Volume de Intel 64 et IA-32 Architectures Software Developer : Guide de programmation du système, partie 1](http://go.microsoft.com/fwlink/?LinkId=148923) (http://go.microsoft.com/ fwlink / ? LinkId = 148923).|  
|**partition enfant**|Toute partition qui est créée par la partition parente (ou racine).|  
|**Core**|Consultez **processeur logique**. **Remarque :** dans ce guide, core est parfois utilisé indifféremment avec un processeur virtuel, en particulier dans les graphiques. Cette utilisation est corrigée dans une future version de ce guide.|  
|**virtualisation de l’appareil**|Une technologie logicielle qui permet un matériel ressources être abstraits et partagé entre plusieurs consommateurs.|  
|**périphérique émulé**|Un périphérique virtualisé qui simule un périphérique matériel physique afin que les invités peuvent utiliser les pilotes par défaut pour ce périphérique matériel. Périphériques émulés sont moins efficaces que les périphériques synthétiques, mais les périphériques émulés prennent en charge pour les systèmes d’exploitation « unenlightened » qui n’ont pas de composants d’intégration.|  
|**connaissances**|Une optimisation pour un système d’exploitation invité prenant en charge des environnements d’ordinateur virtuel et d’ajuster son comportement pour les machines virtuelles. Enlightments aident à réduire le coût de certaines fonctions du système d’exploitation telles que la gestion de la mémoire. Enlightments sont accessibles via l’interface hypercall. E/s compatibles peuvent utiliser le VMBus directement, en ignorant toutes les couches d’émulation de périphérique. Un système d’exploitation qui tire parti de toutes les enlightments possible est dite « entièrement compatibles ».|  
|**système d’exploitation invité**|Le logiciel de système d’exploitation (OS) en cours d’exécution dans une partition enfant. Invités peuvent être un système d’exploitation complet ou un noyau de petite taille, spécial.|  
|**hypercall Interface**|Interface de programmation d’application (API) qui utilisent des partitions à accéder à l’hyperviseur.|  
|**Hyper-V**|Technologie de virtualisation basée sur un hyperviseur pour x64 les versions de [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]. La plateforme de virtualisation Hyper-V permet à plusieurs systèmes d’exploitation isolés partagent une plateforme matérielle unique.|  
|**hyperviseur**|Couche logicielle qui se trouve juste au-dessus du matériel et au-dessous d’un ou plusieurs systèmes d’exploitation. Son rôle principal est de fournir des environnements d’exécution isolés appelées partitions. L’hyperviseur contrôle et détermine l’accès à du matériel sous-jacent.|  
|**interruption**|Un signal asynchrone à partir du matériel indiquant la nécessité d’attention ou d’un événement synchrone dans le logiciel indiquant la nécessité d’une modification de l’exécution.|  
|**Unité de gestion de mémoire d’entrée/sortie (IOMMU)**|Remappe les adresses de mémoire physique pour les adresses qui sont utilisées par la partition enfant|  
|**composants d’intégration (IC)**|Un ensemble de services et les pilotes qui améliorent les performances et l’intégration entre les machines physiques et virtuelles. Composants d’intégration d’activer les systèmes d’exploitation invités à utiliser les périphériques synthétiques, ce qui réduit considérablement la surcharge requise pour accéder aux appareils. Voir aussi **connaissances**.|  
|**services d’intégration**|Consultez **composants d’intégration**.|  
|**processeur logique**|Un processeur qui gère un thread d’exécution (flux d’instructions). Un processeur logique peut être une base ou un thread hyper. Il peut y avoir un ou plusieurs processeurs logiques par cœur (plusieurs si hyper-threading est activé) et un ou plusieurs noyaux par socket de processeur.|  
|**numéro d’unité logique (LUN)**|Nombre utilisé pour identifier un disque sur un contrôleur de disque donné ou au sein d’un réseau SAN.|  
|**partition parente**|Consultez **de la partition racine**.|  
|**partition**|Un ordinateur virtuel (VM) créé par le logiciel de l’hyperviseur. Chaque partition possède son propre ensemble de ressources matérielles (processeur, mémoire et des périphériques). Partitions peuvent posséder ou partager des ressources matérielles.|  
|**l’accès au disque direct**|Représentation d’un disque physique entier comme un disque virtuel dans l’invité. Les données et les commandes sont « transmises » sur le disque physique (via la pile de stockage natif de la partition racine) avec aucun traitement concerné par la pile virtuelle.|  
|**partition racine**|Une partition qui est créée en premier et le propriétaire de toutes les ressources que l’hyperviseur n’est pas propriétaire, y compris la plupart des périphériques et la mémoire système. Il héberge la pile de virtualisation et crée et gère les partitions enfants. La partition racine est également connu sous le nom de la partition parente.|  
|**réseau de zone de stockage (SAN)**|Les réseaux SAN sont des réseaux de périphériques de stockage. Un réseau SAN connecte (généralement) plusieurs serveurs et périphériques de stockage sur un réseau optique Fibre à haut débit unique.|  
|**périphérique synthétique**|Un périphérique virtualisé avec aucun matériel physique analogique afin que les invités n’avez pas besoin d’un pilote (client du service de virtualisation) à ce périphérique synthétique. Pilotes pour les périphériques synthétiques sont inclus avec les composants d’intégration (enlightments) pour le système d’exploitation invité. Les pilotes de périphérique synthétique utilisent le VMBus pour communiquer avec le logiciel du périphérique virtualisé dans la partition racine.|  
|**disque dur virtuel (VHD)**|Un disque dur virtuel est un fichier stocké sur le système de disque native de l’ordinateur physique. À partir d’un ordinateur virtuel, le disque dur virtuel apparaît comme s’il s’agissait d’un disque dur physique. Disques durs virtuels sont basés sur la spécification de Format d’Image de disque dur virtuel. Pour plus d’informations sur la spécification de Format de disque dur virtuel, consultez [http://go.microsoft.com/fwlink/?LinkId=122975](http://go.microsoft.com/fwlink/?LinkId=122975).|  
|**machine virtuelle (VM)**|Un ordinateur virtuel qui a été créé par l’émulation logicielle et présente les mêmes caractéristiques qu’un ordinateur réel.|  
|**service de gestion de machine virtuelle (VMM)**|Les moniteurs d’ordinateurs virtuels fait partie de l’interface du fournisseur de la virtualisation Windows Management Instrumentation (WMI). Outils de gestion de se connecter à ce service pendant l’exécution pour collecter des données sur les partitions actives.|  
|**processus de travail de machine virtuelle (VMWP)**|Chaque machine virtuelle a un processus de travail qui s’exécute dans la partition parente. VMWPs exécuter du code pour enregistrer l’état, l’accès aux périphériques émulés et contrôle de la machine virtuelle.|  
|**processeur virtuel**|Abstraction virtuelle d’un processeur qui est planifiée pour s’exécuter sur un processeur logique. Une machine virtuelle peut avoir un ou plusieurs processeurs virtuels.|  
|**client du service de virtualisation (VSC)**|Un module logiciel chargé par un invité pour utiliser une ressource ou un service. Pour les périphériques d’e/s, le client de service de virtualisation peut être un pilote de périphérique chargé par le noyau du système d’exploitation.|  
|**fournisseur de services de virtualisation (VSP)**|Un fournisseur, exposé par la pile de virtualisation, qui fournit des ressources ou des services tels que les e/s pour une partition enfant.|  
|**pile de virtualisation**|Une collection de composants logiciels dans la partition racine qui coopèrent pour prendre en charge des machines virtuelles. La pile de virtualisation fonctionne avec et se situe au-dessus de l’hyperviseur. Il fournit également des fonctionnalités de gestion.|  
|**VMBus**|Un mécanisme de communication basée sur le canal utilisé pour l’énumération de communication et d’appareils inter-partition sur les systèmes avec plusieurs partitions virtualisées actives.|