## ML for Health Keynote (Fei-Fei Li): Illuminating the Dark Spaces of Healthcare

AI & healthcare is already well studied - allow me to turn everyone’s attention to the physical space of healthcare delivery: in the interaction of the physicians and patients. ICUs, surgery rooms, at home, in the lab.

Example “dark spaces”:
* Surgical operations mistakes: procedural mistakes, accidents, rusty equipment
* ICU mistakes: empty IVs, central line agitation, non-sterile tools
* Senior living: undetected falls, insufficient mobility, abnormal diets, sleep monitoring, incorrect medication
* Pharamcy: wrong prescriptions, supply shortages

Hospital hand hygiene
* Hospital acquired infections kills more people than car accidents every year. Affects 1 in 20.
* Hand hygiene is the leading cause.
* Old school solution: “Secret shoppers”. Very laborious, sparse, and biased.
* Computer vision to the rescue!
* Many vision tasks can benefit from 3d information (pose estimation)
* Depth sensors preserve privacy - you can’t see who the people are.
* 3 challenges in this project, all now pretty much solved:
    * Learning the hand hygiene motion. Mostly straightforward CNN with pose estimation and spatial/angle estimation components. Much better than humans at false negatives, 100% coverage (vs 2 hour windows from human auditors). Transfer learning across hospitals works great, too.
    * Long-range tracking across hallways of hospital. Physicians move around a ton.
    * Dealing with unusual sensor orientation. Viewpoint of camera is often whatever is out of the way - often ceiling looking down. Viewpoint invariant pose recognition from extreme angles. Depth images, point cloud, embed these points into vectors, worth finding this and reading.
* Next step: build a system to actually change clinician’s behavior.

ICU optimization
* Motivation: How to assign correct cost? “How much time is spent for a nurse to do charting, vs measuring vitals, vs emergency help? We don’t really know, but this information is extremely important for hospital to optimize operations and combat errors”
* ICUs are extremely busy.
* Even if you assume offline training can be as expensive as you need it, online video inference is expensive and therefore difficult. So high motivation to build faster video-based action recognition. Current paradigm: dense processing, but we can’t afford it in real world.
* Model for efficient action detection: classify beginning and ending of action, and try to classify hypothesis as good action or not. Good because this method skips lots of frames - classifier jumps candidate start/end frames around a lot.
* On par with dense SOTA (but honestly everyone is pretty bad), but only use 2% of frames.
* Next task: take this into the ICU, automatically detect ICU events. Explainability is also extra important.

Independent senior living
* Senior population growing super rapidly; costs are becoming unsustainable.
* Accidental falls cost ~40B per year.
* A few activities really define quality of life for seniors: mobility (falls, slow movement, unstable gesture, lack of socialization - causes more death than smoking cigarettes), infection (fever, urinary frequency), sleep, diet. Many of these are related to CV, might be able to help.
* Existing wearables/self-monitoring devices are cumbersome. Maybe we can install devices into senior homes to help - ON LOK leading the way here. Installed sensors to detect falls.
* Multisensor! Depth and thermal sensors complement each other - depth for pose estimation, thermal for identifying the person.
* Two technical challenges for this project:
    * Lack of labeled data (self-supervised way to explore coming out in CVPR)
    * Lack rare event data (falls are not that common)
