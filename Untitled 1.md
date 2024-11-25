iowLast login: Wed Nov 20 09:27:06 on ttys001

  

The default interactive shell is now zsh.

To update your account to use zsh, please run `chsh -s /bin/zsh`.

For more details, please visit https://support.apple.com/kb/HT208050.

ncbimac2211:~ manzog2$ ssh cbb

ssh: Could not resolve hostname cbb: nodename nor servname provided, or not known

ncbimac2211:~ manzog2$ ssh cbbdev

ssh: Could not resolve hostname cbbdev: nodename nor servname provided, or not known

ncbimac2211:~ manzog2$ ssh ncbi

ssh: Could not resolve hostname ncbi: nodename nor servname provided, or not known

ncbimac2211:~ manzog2$ ssh manzog2@cbbdev

ssh: Could not resolve hostname cbbdev: nodename nor servname provided, or not known

ncbimac2211:~ manzog2$ ssh manzog2@cbbdev.nih.gov

ssh: Could not resolve hostname cbbdev.nih.gov: nodename nor servname provided, or not known

ncbimac2211:~ manzog2$ ssh 

.CFUserTextEncoding  .idlerc/             Desktop/

.DS_Store            .ipython/            Documents/

.Trash/              .jupyter/            Downloads/

.bash_history        .lesshst             Library/

.bash_profile        .ollama/             Movies/

.bash_sessions/      .ssh/                Music/

.config/             .viminfo             Pictures/

.cups/               .vnc/                Public/

.git/                .vscode/             pivtmp/

.gitconfig           Applications/        

ncbimac2211:~ manzog2$ ssh 

.CFUserTextEncoding  .idlerc/             Desktop/

.DS_Store            .ipython/            Documents/

.Trash/              .jupyter/            Downloads/

.bash_history        .lesshst             Library/

.bash_profile        .ollama/             Movies/

.bash_sessions/      .ssh/                Music/

.config/             .viminfo             Pictures/

.cups/               .vnc/                Public/

.git/                .vscode/             pivtmp/

.gitconfig           Applications/        

ncbimac2211:~ manzog2$ ssh 

.CFUserTextEncoding  .idlerc/             Desktop/

.DS_Store            .ipython/            Documents/

.Trash/              .jupyter/            Downloads/

.bash_history        .lesshst             Library/

.bash_profile        .ollama/             Movies/

.bash_sessions/      .ssh/                Music/

.config/             .viminfo             Pictures/

.cups/               .vnc/                Public/

.git/                .vscode/             pivtmp/

.gitconfig           Applications/        

ncbimac2211:~ manzog2$ ssh manzog2@

@::1                             @linkerd.be-md

@broadcasthost                   @linkerd.be-md.ncbi.nlm.nih.gov

@linkerd                         @localhost

ncbimac2211:~ manzog2$ ssh manzog2@

@::1                             @linkerd.be-md

@broadcasthost                   @linkerd.be-md.ncbi.nlm.nih.gov

@linkerd                         @localhost

ncbimac2211:~ manzog2$ ssh manzog2@

@::1                             @linkerd.be-md

@broadcasthost                   @linkerd.be-md.ncbi.nlm.nih.gov

@linkerd                         @localhost

ncbimac2211:~ manzog2$ ssh manzog2@

@::1                             @linkerd.be-md

@broadcasthost                   @linkerd.be-md.ncbi.nlm.nih.gov

@linkerd                         @localhost

ncbimac2211:~ manzog2$ ssh manzog2@cbbded11

ssh: Could not resolve hostname cbbded11: nodename nor servname provided, or not known

ncbimac2211:~ manzog2$ ssh manzog2@cbbded12

ssh: Could not resolve hostname cbbded12: nodename nor servname provided, or not known

ncbimac2211:~ manzog2$ ssh manzog2@cbbdev

ssh: Could not resolve hostname cbbdev: nodename nor servname provided, or not known

ncbimac2211:~ manzog2$ ssh manzog2@cbbdev11

The authenticity of host 'cbbdev11 (130.14.25.31)' can't be established.

ECDSA key fingerprint is SHA256:CivPqCZsgKtRGKMI127k4dH8H30zZ1dM7dRtvp/F/qE.

This key is not known by any other names.

Are you sure you want to continue connecting (yes/no/[fingerprint])? yes

Warning: Permanently added 'cbbdev11' (ECDSA) to the list of known hosts.

manzog2@cbbdev11's password: 

Permission denied, please try again.

manzog2@cbbdev11's password: 

Received disconnect from 130.14.25.31 port 22:2: Too many authentication failures

Disconnected from 130.14.25.31 port 22

ncbimac2211:~ manzog2$ 

ncbimac2211:~ manzog2$ ssh manzog2@cbbdev11

manzog2@cbbdev11's password: 

Permission denied, please try again.

manzog2@cbbdev11's password: 

Received disconnect from 130.14.25.31 port 22:2: Too many authentication failures

Disconnected from 130.14.25.31 port 22

ncbimac2211:~ manzog2$ ssh manzog2@cbbdev11

manzog2@cbbdev11's password: 

Last failed login: Thu Nov 21 12:56:29 EST 2024 from ncbimac2211.be-md.ncbi.nlm.nih.gov on ssh:notty

There were 2 failed login attempts since the last successful login.

  

* This warning banner provides privacy and security notices consistent

  with applicable federal laws, directives, and other federal guidance

  for accessing this Government system, which includes (1) this computer

  network, (2) all computers connected to this network, and (3) all

  devices and storage media attached to this network or to a computer

  on this network.

  

* This system is provided for Government-authorized use only.

  

* Unauthorized or improper use of this system is prohibited and may

  result in disciplinary action and/or civil and criminal penalties.

  

* Personal use of social media and networking sites on this system is

  limited as to not interfere with official work duties and is subject

  to monitoring.

  

* By using this system, you understand and consent to the following:

  

   * The Government may monitor, record, and audit your system usage,

     including usage of personal devices and email systems for official

     duties or to conduct HHS business. Therefore, you have no reasonable

     expectation of privacy regarding any communication or data transiting

     or stored on this system. At any time, and for any lawful Government

     purpose, the government may monitor, intercept, and search and

     seize any communication or data transiting or stored on this system.

  

   * Any communication or data transiting or stored on this system

     may be disclosed or used for any lawful Government purpose.

  

***** NCBI-TESTING HOST *****

  

  This host is in the "guinea pig" class. It will receive updates to system

packages [usually one week] prior to deployment on all hosts. This provides

the opportunity to vet changes on a small subset of machines and catch issues

early. If you find an issue related to a software change, please inform:

unix.systems@ncbi.nlm.nih.gov

  

******************************

  

Generating NCBI shell config files

Generating NCBI Config files from /home/manzog2/.ncbi_hints ...

Enabled facilities: cmake ctags ddd developer gcc git joe ncbi_developer ncbi_tools nedit ninja subversion svnmucc

Done! Total time to generate: 0.00542 seconds

Sourcing NCBI config file...

done.

[manzog2@cbbdev11 ~]$ ls

[manzog2@cbbdev11 ~]$ cd ..

[manzog2@cbbdev11 home]$ ls

abergeris      dettmannsn    jcherry         mcveigh      simonett

agarwala       dharkerns     jianye          mcwillia     simonyan

akimchi        dicuccio      jirlesec        mekhedov     sinyakov

akinpelu       didenkom      joardarv        merezhuk     sirotkin

akintunjima    dikunovs      johnston        michael      slagleers

allenla        dipasqualesm  jxiao           mieg         smithdb

altschul       dlewis        kann            mjohnson     smithtg

alves          dobbinshd     kans            monacomk     sommerszm

ananthar       doerr         karmanov        montour      song

anderson       domagalskimj  kawolf          morganp      sorgecf

andrewsg       domrach       kelly           morgulis     soussov

anguyen        dukhanin      keranahallipb   mosunmadero  sporgitasa2

aprasad        dukisf        khajar          moyered      spouge

asztalos       dunivin       khotomli        murciami     starchen

auslandern2    durkinas      khromovo        murphy       stolern

babajanyans2   dzhang        kiryutin        mxu          sukharni

bagherih       engelson      kishchuk        myerskr2     suzek

baileysd       eskandar      klimke          nagarajanm2  tang

balasano       evgeniev      kobiashviliv2   natxie       tatiana

barrett        faureg        kodalivk        nawrocke     taylorml

bauer          federhen      kolotev         noemn        teferism

bealer         feldgard      konizercg       oakleycd     thierryd

beckerje       fialkov       koonin          omelchen     tholejf

beloslyu       fineam        korobtch        osipov       tians2

belyi          fingerma      korovkin        osobaka      timonin

bihanm         fleshman      kostyukovskya   ostapchu     todorov

bollin         friedman      kotliaro        ostell       tolstoy

bolton         frimanav      kubasik         osulliva     torrese2

borkaraa       frisse        kuc3            parantha     travers

bornsteinkl    frost         kuznets         park         trivedise

borodine       gaasterl      lakshmin        patterso     tufanotl

boshkina       gasiored      lanczyck        pembertoncg  ucko

bouffard       glodeka       landsman        pengy6       ukrainch

brendlingerld  goldft        lapointr        persie       vanderve

brennan1       gonceare      lashmano        pierovbg     vasilche

brinkam        gorelen       lavr            przytyck     vasilyev

brodskyd       gotvyans      lawrenceema     pwolf        venkatapathyr2

brown          gravessh      leem28          racheva      veraalva

brucheyks      greenbergnal  leeyc           raear        viswanl

bryant         grisha        leipe           raina        vitekms

bryzguno       haftdh        leubsdor        rajput       wangk5

camacho        hamelers      lewis           randy        wangq2

carmel         hamilto5      lewiskj         ranganat     weber

carolyn        hanzhen       lillian         rangwala     weic4

catipone       hao           liuh2           raynerar     weinber3

cavanaug       hart          liw13           renata       whlavina

chakravartyd2  hatchere      lotovv          resenchu     wilbur

chenc8         he            lozitski        rezaiet      willialm

chenhc         henselns      lsmith          riley        william10

chenj          hiraparasd    luabeyam        rodarme1     williamsre

chitsaz        hoeppner      luojaa          roosen       wojtyniakm

chlumsky       hoffman       madans2         rosentha     wwu

churchs        hohmann1      madden          roxasrm      xul12

clarkdanl      howard        madej           sadyrovr     yaghih2

cliu           hugheyjn      mahamaa2        sampson1     yangs5

cloughea       hunge2        maitir          sapojnik     yangy39

colsonp        hurwitz       mallepulap2     sarkisov     yaog2

comeau         iazvovsk      maloneylopezmc  schuler      yaschenk

cook           ibecc         managdav        scott        yazhuk

cooperboj      ihlenfel      manberu         seebadan     yeganova

coulouri       irvingad      manzog2         serena       yual

coxe2          iskhakov      manzouro        serovan      yub5

dab            islamaj       marcanto        setoct       yuk6

davenpor       israeler      marchler        shaninna     yyu

daytb          ivanchen      marino          shaytana     zapatarm

dean           ivanov        masterso        shkeda       zasypkin

deminp         ivanovs1      mbasu           shutovic     zellerse

dernovoy       jane          mcginle1        shutovo

[manzog2@cbbdev11 home]$ cd ..

[manzog2@cbbdev11 /]$ ls

MegaSAS.log          hs_err_pid18913.log  hs_err_pid31240.log

am                   hs_err_pid19307.log  hs_err_pid31271.log

bin                  hs_err_pid19336.log  hs_err_pid31669.log

boot                 hs_err_pid19364.log  hs_err_pid31698.log

dev                  hs_err_pid19537.log  hs_err_pid31726.log

dropbox              hs_err_pid19565.log  hs_err_pid31812.log

etc                  hs_err_pid19593.log  hs_err_pid31841.log

export               hs_err_pid19740.log  hs_err_pid31869.log

home                 hs_err_pid19771.log  hs_err_pid31917.log

hs_err_pid10292.log  hs_err_pid19802.log  hs_err_pid31960.log

hs_err_pid10320.log  hs_err_pid19933.log  hs_err_pid31990.log

hs_err_pid10349.log  hs_err_pid19961.log  hs_err_pid32026.log

hs_err_pid10658.log  hs_err_pid19990.log  hs_err_pid32054.log

hs_err_pid10686.log  hs_err_pid20470.log  hs_err_pid32082.log

hs_err_pid10714.log  hs_err_pid20503.log  hs_err_pid32292.log

hs_err_pid10885.log  hs_err_pid20531.log  hs_err_pid32320.log

hs_err_pid10915.log  hs_err_pid20584.log  hs_err_pid32348.log

hs_err_pid10943.log  hs_err_pid20603.log  hs_err_pid32534.log

hs_err_pid11243.log  hs_err_pid20614.log  hs_err_pid32562.log

hs_err_pid11271.log  hs_err_pid20631.log  hs_err_pid32590.log

hs_err_pid11300.log  hs_err_pid20642.log  hs_err_pid33269.log

hs_err_pid11475.log  hs_err_pid20659.log  hs_err_pid33297.log

hs_err_pid11503.log  hs_err_pid2075.log   hs_err_pid4262.log

hs_err_pid11531.log  hs_err_pid20793.log  hs_err_pid4325.log

hs_err_pid11895.log  hs_err_pid20821.log  hs_err_pid4356.log

hs_err_pid11923.log  hs_err_pid20849.log  hs_err_pid5242.log

hs_err_pid11951.log  hs_err_pid2107.log   hs_err_pid5270.log

hs_err_pid12172.log  hs_err_pid2137.log   hs_err_pid5301.log

hs_err_pid12201.log  hs_err_pid21403.log  hs_err_pid5483.log

hs_err_pid12229.log  hs_err_pid21432.log  hs_err_pid5489.log

hs_err_pid12315.log  hs_err_pid21460.log  hs_err_pid5511.log

hs_err_pid12346.log  hs_err_pid21549.log  hs_err_pid5521.log

hs_err_pid12378.log  hs_err_pid21580.log  hs_err_pid5541.log

hs_err_pid1253.log   hs_err_pid21608.log  hs_err_pid5549.log

hs_err_pid12722.log  hs_err_pid22407.log  hs_err_pid5634.log

hs_err_pid12746.log  hs_err_pid22435.log  hs_err_pid5639.log

hs_err_pid12750.log  hs_err_pid22463.log  hs_err_pid5667.log

hs_err_pid12774.log  hs_err_pid23544.log  hs_err_pid5671.log

hs_err_pid12778.log  hs_err_pid23572.log  hs_err_pid5695.log

hs_err_pid12802.log  hs_err_pid23601.log  hs_err_pid5702.log

hs_err_pid1281.log   hs_err_pid23725.log  hs_err_pid5803.log

hs_err_pid12840.log  hs_err_pid23753.log  hs_err_pid5839.log

hs_err_pid12868.log  hs_err_pid23781.log  hs_err_pid5867.log

hs_err_pid12896.log  hs_err_pid24064.log  hs_err_pid6512.log

hs_err_pid12965.log  hs_err_pid24095.log  hs_err_pid6541.log

hs_err_pid13085.log  hs_err_pid24123.log  hs_err_pid6571.log

hs_err_pid1309.log   hs_err_pid25044.log  hs_err_pid691.log

hs_err_pid13122.log  hs_err_pid25072.log  hs_err_pid6931.log

hs_err_pid13247.log  hs_err_pid25100.log  hs_err_pid6961.log

hs_err_pid13280.log  hs_err_pid25709.log  hs_err_pid6969.log

hs_err_pid13308.log  hs_err_pid25739.log  hs_err_pid6989.log

hs_err_pid13656.log  hs_err_pid25767.log  hs_err_pid7002.log

hs_err_pid13684.log  hs_err_pid26019.log  hs_err_pid7030.log

hs_err_pid13712.log  hs_err_pid26049.log  hs_err_pid7036.log

hs_err_pid1387.log   hs_err_pid26077.log  hs_err_pid7072.log

hs_err_pid14131.log  hs_err_pid2610.log   hs_err_pid7101.log

hs_err_pid1416.log   hs_err_pid26343.log  hs_err_pid719.log

hs_err_pid14161.log  hs_err_pid26374.log  hs_err_pid7391.log

hs_err_pid14189.log  hs_err_pid2638.log   hs_err_pid7419.log

hs_err_pid14252.log  hs_err_pid26403.log  hs_err_pid7450.log

hs_err_pid14281.log  hs_err_pid26453.log  hs_err_pid750.log

hs_err_pid14310.log  hs_err_pid26481.log  hs_err_pid7820.log

hs_err_pid1444.log   hs_err_pid26509.log  hs_err_pid7857.log

hs_err_pid14886.log  hs_err_pid2667.log   hs_err_pid7885.log

hs_err_pid14915.log  hs_err_pid2677.log   hs_err_pid8246.log

hs_err_pid14944.log  hs_err_pid26823.log  hs_err_pid8274.log

hs_err_pid15574.log  hs_err_pid26852.log  hs_err_pid8305.log

hs_err_pid15602.log  hs_err_pid26880.log  hs_err_pid8680.log

hs_err_pid15630.log  hs_err_pid26985.log  hs_err_pid8708.log

hs_err_pid16237.log  hs_err_pid27013.log  hs_err_pid8736.log

hs_err_pid16322.log  hs_err_pid27041.log  hs_err_pid9029.log

hs_err_pid16339.log  hs_err_pid2705.log   hs_err_pid9057.log

hs_err_pid16350.log  hs_err_pid27161.log  hs_err_pid9085.log

hs_err_pid16367.log  hs_err_pid27189.log  hs_err_pid9573.log

hs_err_pid16398.log  hs_err_pid27217.log  hs_err_pid9601.log

hs_err_pid16442.log  hs_err_pid2733.log   hs_err_pid9629.log

hs_err_pid16474.log  hs_err_pid27823.log  hs_err_pid9764.log

hs_err_pid16502.log  hs_err_pid27851.log  hs_err_pid9788.log

hs_err_pid16555.log  hs_err_pid27879.log  hs_err_pid9795.log

hs_err_pid16588.log  hs_err_pid28544.log  hs_err_pid9817.log

hs_err_pid16618.log  hs_err_pid28572.log  hs_err_pid9823.log

hs_err_pid16792.log  hs_err_pid28600.log  hs_err_pid9845.log

hs_err_pid16820.log  hs_err_pid28874.log  lib

hs_err_pid16848.log  hs_err_pid28930.log  lib64

hs_err_pid17305.log  hs_err_pid28960.log  media

hs_err_pid17333.log  hs_err_pid29696.log  mnt

hs_err_pid17361.log  hs_err_pid29726.log  net

hs_err_pid17609.log  hs_err_pid29761.log  netmnt

hs_err_pid17637.log  hs_err_pid30026.log  netopt

hs_err_pid17665.log  hs_err_pid30060.log  opt

hs_err_pid17992.log  hs_err_pid30095.log  panfs

hs_err_pid18020.log  hs_err_pid30517.log  proc

hs_err_pid18048.log  hs_err_pid3052.log   root

hs_err_pid18213.log  hs_err_pid30546.log  run

hs_err_pid18241.log  hs_err_pid30574.log  sbin

hs_err_pid18272.log  hs_err_pid30681.log  srv

hs_err_pid18592.log  hs_err_pid30709.log  sys

hs_err_pid18620.log  hs_err_pid30737.log  tmp

hs_err_pid18651.log  hs_err_pid3081.log   usr

hs_err_pid18856.log  hs_err_pid3109.log   var

hs_err_pid18885.log  hs_err_pid31208.log

[manzog2@cbbdev11 /]$ cd net

[manzog2@cbbdev11 net]$ ls

frosty  intdev  traces04-d8

[manzog2@cbbdev11 net]$ cd intdev/

[manzog2@cbbdev11 intdev]$ ls

ls: cannot access artifactory_dev: Permission denied

ls: cannot access artifactory_data: Permission denied

aceview01           clintest      irbsys               pubmed_mti

alt_splicing        data-copy     lulab                pubtator

aptamers            dbGaP-Temp    lulab_archive        qmbp

aptax               devdcode      mapfiles             rapt

artifactory_data    discovery     metagut              sra-test

artifactory_dev     eztest        mgv_assets           svat_mcgv_temp

baby                flycellatlas  oblast01             svnalma8test

bacteria_mutations  gap           pathogens            tar-2-archive

bbkt-rec-data       genome_maint  pmc-archive-staging  tax_analysis

bioproject          genomebuild   pmc-attic            taxdata

cbb01               gtbridge      pmc_dev              test_gbrelease

cbb02               hmgn_mouse    pnbr_work            usability_testing

cbb03               homologene    ppmcqa               variation

centos-backup       htseq         projects             varpipe01

chromatin_hic       iebqa         publog               vvflow

[manzog2@cbbdev11 intdev]$ cd devdcode/

[manzog2@cbbdev11 devdcode]$ ls

ARCHIVE                             di                          mehariz

Atlas-of-TFBS-from-ENCODE-DHS-data  enhancer_DL_methods_2.pptx  sanjar

EpiMap-GeneEnhancerLink-Data        gaetano                     wei

EpiMap-TraitTissue-Enrichment       ivan                        xiaoqin

common                              jaya

[manzog2@cbbdev11 devdcode]$ cd gaetano/

[manzog2@cbbdev11 gaetano]$ ls

bedtools-2.29.1.tar.gz  bios_mapping_sample         peak_files

bedtools2               control_wgs.bed             training_files

bios_mapping            generate_training_files.sh

[manzog2@cbbdev11 gaetano]$ vi generate_training_files.sh 

[manzog2@cbbdev11 gaetano]$ cd bios_mapping_sample 

-bash: cd: bios_mapping_sample: Not a directory

[manzog2@cbbdev11 gaetano]$ ls

bedtools-2.29.1.tar.gz  bios_mapping         control_wgs.bed             peak_files

bedtools2               bios_mapping_sample  generate_training_files.sh  training_files

[manzog2@cbbdev11 gaetano]$ vi generate_training_files.sh 

  

#o $line |cut -d" " -f3)i/bin/bash

#########################################################################################################################################################

#       The metadata CSV file "hg38_bedfiles.csv" contains 7845 ENCODE4 files with DNAse/ATAC-/ChIP-Seq data. Redundant files were removed using        #

#       the script filter_metadata.py. 4386 unique files were recovered. These will be used to generate input files for TREDNet.                        #

#       

#########################################################################################################################################################

  

**mapping_file**=/net/intdev/devdcode/gaetano/bios_mapping_sample

**exons**=/net/intdev/devdcode/common/CenTRED/training_files/hg19_files/output_ENSG_exon.txt.UCSC.onetss

**blacklist**=/net/intdev/devdcode/common/CenTRED/training_files/hg19_files/wgEncodeDacMapabilityConsensusExcludableBlacklist.bed

**promoters**=/net/intdev/devdcode/common/CenTRED/training_files/hg19_files/output_ENSG_promoter.UCSC.alternativetss

  

while IFS= read -r line; do

        **biosample**=$(echo $line |cut -d" " -f1)

        **DNase_accession**=$(echo $line |cut -d" " -f2)

        **DNase_file**=$DNase_accession.bed

        **H3K27ac_accession**=$(echo $line |cut -d" " -f3)

        **H3K27ac_file**=$H3K27ac_accession.bed

        **H3K4me1_accession**=$(echo $line |cut -d" " -f4)

        **H3K4me1_file**=$H3K4me1_accession.bed

        echo $biosample

  

  

        **DNase**=/net/intdev/devdcode/gaetano/peak_files/hg19/multi-label/DHSse-Seq/$DNase_file

        **H3K27ac**=/net/intdev/devdcode/gaetano/peak_files/hg19/multi-label/H3K27ac/$H3K27ac_file

        **H3K4me1**=/net/intdev/devdcode/gaetano/peak_files/hg19/multi-label/H3K4me1/$H3K4me1_file

  

                                                                                                                    1,8           Top