## Computational Methods ofr Solving Developing World Problems

Two problems:
* Lack of expert labor
* Lack of actionable data

Data Science Africa conference - tries to describe unique problems in Africa.
Potential uses and datasets
Agriculture
* disease monitoring - takes about 6 months to turn surveillance into actionable map. ML can make this intelligence arrive in near real-time.
* Farmers take a picture of their garden, upload the picture, unlabeled.
    * They tried asking farmers for labels, but it was mostly to calibrate how well they knew the diseases.
* Incentivizing farmers to do this is tricky - they need data airtime
    * Attempts to incentivize: rockstar, ranking them ("this guy is a rockstar!”), social workers
* Diagnosis of leaf images (disease, severity)
* Example tasks:
    * Automated whitefly count. There can be hundreds of them on a leaf, you need to take several samples - task is infuriating.
    * Necrosis measurement of roots

Human Health
* Automated lab diagnostics
* Many require phone/microscope attachments - 3d printing these is cheap
* Example tasks:
    * Automate diagnosis of malaria from blood slides/microscope. Typically you count them by hand, but there are more microscopes than experts. Solution is to put it on a mobile phone (through the eyepiece of the microscope). But this is currently done with thick blood slides, accuracy is in the high 90s; thin blood slides would be an improvement.
    * Tuberculosis bacili in sputum
    * Worms in fecal matter

Radio mining: "the real social media of Uganda"
* People calling in and reporting things that happened or airing grievances
* Capture data with an antenna and a microphone

Telecoms data:
* Aggregate statistics of movement based on Call Data Records (CDR)
* Hard to get this data, private, so they use aggregated & anonymized data.
* Example usage:
    * Understanding a typhoid outbreak - where the epicenter was, how it moved.

Poverty and the environment with satellite imagery
* Tasks:
    * Car counting to estimate populations for planning purposes. This is more accurate than counting houses.

Thoughts on deployment/challenges
* Low expectations
    * Don’t come in expecting to change the world
* High expectations
    * Dunning-Kruger effect: people can really overestimate ML’s power once they get a taste of it
    * Pilotitis: they do endless pilots
* Data issues: access, representativeness, privacy
* Theory-practice tradeoff: DL is often too expensive in practice
* Quality control
* Bureaucracy

Final note: collaborator/stakeholder involvement is key: efforts without these never work

Scale of these efforts: there are maybe 5 students at the university in Kumpala, Uganda; maybe 8 in another university (Jakarta?)
