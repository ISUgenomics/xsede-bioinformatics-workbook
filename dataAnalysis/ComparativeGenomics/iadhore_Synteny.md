# Synteny with iadhore 3.0.01

First there are two types of synteny.
1.  Is using DNA to DNA alignments to identify conserved genomic fragments.  
2.  Is to use gene sequences only, to identify conserved gene order.   

Both types of synteny are useful for inferring chromosomal rearrangements and for identifying highly conserved genes. The first type of synteny is only appropriate for very closely related organisms, as nucleotide similarity is quickly lost when species diverge.  The second type of synteny is useful for finding conserved chromosome fragments in more divergent species. This allows for lots of change in intergenic regions, while we can rely more on evolutionary constrained genes to infer conserved gene order.

Iadhore is a program that uses gene order to identify synteny, and thus can be leveraged in many species comparisons.

First step here is to have a list of orthologs between your two targeted species already calculated.  This can be done with blast, opscan, orthoMCL, etc.  For this tutorial, I will be using the prerequisite files (operon.db and genome.db) as well as the  orthologs that were calculated in the OpscanOrthologCaller tutorial.

### Obtain prerequisite files
genome.db
```
>g1 1 1923 1 + 000085K
CQPAFNSTQHQHQCAPSSSTHFVATTHHFIMSDMSAYMGSGPAEPAPSSGAAEASPSSGVASAYMGSGPAEPAPSSGAAEASPSSGVASAYMGASPAYEPPAQEKSPDQSAYMFIIAVKNEEEHQQNRLRPYEIDPTRGIAERPRLKKYLRNDEAIRRLVIDFDHKENKNQADIINHIHALQYRLGMKGFEEWD
>g2 1 2912 2263 + 000085K
MGRGAHLPEDPQPRPRPCRWPTQAKLAGTSGFFVQLDELYKTVSMAAFRFAFPDGRSPPVPPLSVILRQSLLANHSKFRQEPEKLRHFYDNGETNAFMRSTFRDDQHSKKIVMGNGGGGEKEEKREDEKRK
>g3 1 6346 3036 - 000085K
MSSVRSISSTARAGNVLVLLDLYASGFASSNTSPTIPMLTSRTISFPLNFWLAMLLVIASISGTMLIILLMNAFAHRLDITVHKNGLAVIIEAFLEWLYGFNNFRVAFLFMLLHDAPITLANFFLLGACRCAGPNVLSWPLLLSALAIALSLCWRLLLLRFAYARLVFRRPSPDPNSAFPSRSHSFRQQFAADQCTASQNEVNSQLDELWAIRRARAIVYGEKRGKCWEGTAGETLYLGEEEEGARGTGRSMGQCCGFWSSWVLLKGFDLFCALCRRLLCLLLSLFLCSVCLSVGCVPCLHHYSCSPNSFSHRHKCAKTFVRHFSLLFHYVIFGFSLCFSALLILLNVVLIFSTQLVGPNQWPPEISRLCISVSPHRRIVRPLFLPQSSLFSSFLLPPKQMNNGTAADLRSHSLVQCKPIWDLPHQQTLVDKWAPGLSRKSPSPWQSRFPLQDGRVLAVSTHFVSDHSEEQSPCHTLFYDFALLTVGADNSSKTTKCARQRSSGWFFANARNVLAFPYFWACSPSISIRKGTLINCQSLTKH
>g4 1 9212 7856 - 000085K
MNAFCSAPSEGPVTIELRQKIVDFFKPEHLEVECESRLHNVPKGAEKHFRVQIVSDKFNGMTQLHRQRMVNKLLAEELREKIHALRIEAKIPSEWHGTKQTPAPPCEGGEKKRRQSEQPKRQ
>g5 1 14129 11906 - 000085K
MLSPLASSSSARPSYSRHHKQSTYFHRPTLIKSEPEELCSSVPPVSSLSSSSSLSSSSSSSSSSLSSSSLSSSSKSLVPKQLRPPPLIDTSTPESLERDFHAWLKGELSRSERPFCARHSDCFSAQSPPPSAMFLTPLGNVKNELVVCPTDFGGDFVFGMELEPSNSDFCASTAAFAPSISMNGPFPPMQTQMIRMPMPSLSASITQEDQQMAYLLSSAGQSPSGSSQHSSLEGSPLQPNCHQTMLLSIGKYELNDRKMLTELSGEVKTDGAKKMAATDAAMTAPNSPGGRSSGTNQLGRTYSPGLPLSMVERQKIVQLFHEGWKICDISKYLCVTHSCVSKILQRFRATGSVRPKDAKEGRQESPLVAAIRDYRQRLGIMRQSEIREQLIRDGLCRRENAPSRSSINHILRTKLSGLEAPTIGKRSSNQTTENANGKRQTDGRGENDGTAANAATARVYYDE
etc.
```
operon.db
```
>GPLIN_000000100 1 1060 32 + 1
VGSAGLLCETGGFCPWLRAVSLRGGAWTSGESCLWSASAACMLVRAGVRQESGLSSHARKLHSSEKEARANLHAPRCLSAMPKFTATFEANTLSELLSQIKGVLAEGNSVGVGAKKPSVGEAGGVAKAGGKAAKRKRLRQQAAAAVVAAKHAKGGDEEAAETSEKQVDPSSTKPPKKDKPHRKSLEGKE
>GPLIN_000000200 1 48028 47003 + 1
MSKAAEPLLKDAIISLGPPNSTIVCAVSGHPTSFPQRLCNAIFSKIYELGITILVSKLEGRFLHVQLGSGMDALMALSMDGVVLGEDLRLEVCLGFAGCWLDLLMADLQCLGVVREIRMRKVMNCLAMGKRLFWTMFRSLISPM
>GPLIN_000000300 1 67668 48851 - 1
MADQQQQQQDDLGPPPDPVMEVPPPKEIKVLESADDIQSRRTEVLDHYAQFQGFATIKRERLEEARQFQYFKRDADELEIWILEKLQTAAEESFRDPTNLQAKIQKHEAFVAEVQAHSNAITKLDKTGNDMIQHDHYEKDTIRKRLDRLHELWDRLFAMLEGKGIKLQQTLKLLQFVRKCDEMLYWIRDKIQFVSSDDLGADLEHVEVMQRKFDEFLKELKSHESRVLDINHEANTLIDEGHPEQQQIHGKRDEVNEAWHKLGTLTSTRGEALFGAQQIQRFYRDIDETLAWMGEKELTLATDDYGRDLNNVQALQRKHEGTERDLAALESKMDKLGSETNRLCQLYPEKSGDIATKMDEAKGRWEALKLGAEQRKRGLDRSYNRHRFMADYRELGEWIKGIQALIQSSELAKDVAGAEALLEQHQEHKGEIEARADSFKQTAETGQRLLDEEDIDNAXXXXXXXXXXXXXXXXXXXXXXNLISFLATGAKLQEANQEQLFNRNIEDVELWLSELEGQLASEDFGKDLVSVQNLQKKLGLVESDYNAHQERIDAIGHQTREFHDTGHFNAPLISKKFDVLQQRFEALREPLQRRKQKLAESLLGHQLFRDIDHELAWIREKEQIAASTNRGRDLVGVQNLIKKQNALHTEIANHEQQMEQVAQSAEQMVQRGHFLAPDIRDKKSQLRDNWRALKTKADKRKQDLQDSLQAHQYLADANEAESWMRDKEPLVGSTDYGKDEDSAESLLKKHRALMSDLEAFNTTIEELRKEAGQCKYQEQLGGQLGKECVVALYEYTEKSPREVSMKKGDVLTLLNASNKDWWKVEVSDRQGFVPAAYVKRIEPGSQHHHQAMAGQPMNTINAKQSQSEDQYKRLLMLGEQRKRKLEEACKAYQLLREANDLAEWIRSRETVASQQEIGQDLEQVEVLQNKFNDFKNDLKANEVRLQEMNQIATRLSQMGQTETAVRIRQQIDDLNARWKALEQKAEERGQQLESAHEVQRFHKDVDETKDWIQEKNETLDSEDFGRDLRSVQALQRKHEGVERDLAALGDKIRALDEKANRLRQTHPEAAEQIYDLQRQLNEQWTTLTQKANRRKDKLLDRPCVSMKKGDVLTLLNASNKDWWKVEVSDRQGFVPAAYVKRIEPGSQHHHQAMAGQPMNTINAKQSQSEDQYKRLLMLGEQRKRKLEEACKAYQLLREANDLAEWIRSRETVASQQEIGQDLEQVEVLQNKFNDFKNDLKANEVRLQEMNQIATRLSQMGQTETAVRIRQQIDDLNARWKALEQKAEERGQQLESAHEVQRFHKDVDETKDWIQEKNETLDSEDFGRDLRSVQALQRKHEGVERDLAALGDKIRALDEKANRLRQTHPEAAEQIYDLQRQLNEQWTTLTQKANRRKDKLLDSYGQCFLKAALIEKRSKLGESQTLQQFSRDAERWRIGWRRSSKSRRRRPTGPTNIQQKHQKQQAFEAELSANADRIATLISAGQNLITAAKCGGGETAVSARLRALNDQWEQLVKTTTEKSHRLKEANKQKTFMAAVKDLEFWLGEVETLLASEDYGRDLASIENLLKKHQLLEADITAHADRVEDMNRQADALLESEQFDQAQIDGRRRNINERYERVKDAANVRRDKLNKAITVHQFLRDIDEEESWIKEKKLLVSSDDYGRDLAGVQNLRRKHRRFDTELATHQPQVQVVRSKGMELMASSEIGVPEIVKRIKALDQSWTHMVELTEDRHKKLQESEEFQNFIGRVEEEEAWLNEKQQILSSPNVGENMAAVQGLLKKHDTFEVDLQMHQQRIDELQRQGEELINAGNHHAKNIGTRMEQLVKHLILVKELAVRRLQKLRDNNAYMQFMWKCDVVESWIGDKEPHVRSTDFGRDLSSVQLLLNKQDTFDNGLNNFEHEGIQRVTELKDQLLEAEHEQSAAIEQRHQAVIQRWQQLLMNSLERRKKLTEAQAHFKNIEDLYLTFAKKASAFNSWFENAEEDLTDPVRCNSLEEIREHSTVGLAQAWDQLDQLAMRMQHNLEQQIQARNQSGVSEEALREFSMMFRHFDREKLGRLDHQQFKSCLRALGYDLPMVDEGQPEPEFQRILDLVDPNRDGYVTLQEFMAFMINKETENVRSSEEIEMAFRALSKEFRPYVIAEELFANLTPEQADYCINRMKPYVDAASGRTIAGALDFEQFVQSVFMN
>GPLIN_000000400 1 74810 70588 - 1
MITTRLSTCHCTFVGGFFRSHRSENFKKINKAVNIKCQPRMPKKLLPVTSELKTHFEILLERFLDQKYSQAYLNLFTLYLKTFKQFTAFSEEQAIEALAKLEDFFTKMSLDSEIQLSDLNAQLLTLLKNYDSDERHSWEVSELEQLALYTKHITGNVSDWIQNELEDAWPDELSRAAKNALGIEQISDPYAYNKTAHIIKDAVSSRGVPGFIYTILVSLDWDPIANFWYKCNPDYCFPVKGFHGINFVVLRHEIGSQQRAEQAEKWFEAQKSAMIKTIRDNDKISDLGSLIRKGAKVRRKLEEFAH
etc.
```

OrthologousPairs.list (tab delimited)
```
GPLIN_000000100 g12170
GPLIN_000000200 g11691
GPLIN_000000300 g16041
GPLIN_000000400 g29333
GPLIN_000000500 g21617
GPLIN_000000600 g1861
GPLIN_000000700 g3508
GPLIN_000000800 g17807
GPLIN_000000900 g25809
GPLIN_000001000 g2058
GPLIN_000001100 g17530
GPLIN_000001200 g23779
GPLIN_000001300 g18358
GPLIN_000001400 g5028
GPLIN_000001500 g18095
GPLIN_000001600 g23645
GPLIN_000001700 g25395
etc
```

We now need to create the files necessary for running iadhore.
```
mkdir subject
mkdir query
cd query/
#this creates a file for each scaffold containing gene and strand information
tr "\n" "\t" <../operon.db |sed 's/>/\n>/g'|awk '{print $1$5,$6}'|sed 's/>//g' |awk '{print >> $2 ".lst"; close($2)}'
#gets rid of the extra column
sed -i 's/ .*//g' *.lst
#puts all files in this directory listed in input.txt
ls *lst >input.txt
#Creates the query file for iadhore, scaffold \t folder/file.lst
  paste <(cut -f 1 -d "." input.txt) <(awk '{print "query/"$1}' input.txt)>query.ini

#repeat the same procedure for the subject
cd ../subject/
tr "\n" "\t" <../genome.db |sed 's/>/\n>/g'|awk '{print $1$5,$6}'|sed 's/>//g' |awk '{print >> $2 ".lst"; close($2)}'
sed -i 's/ .*//g' *.lst
ls *lst >input.txt
paste <(cut -f 1 -d "." input.txt) <(awk '{print "subject/"$1}' input.txt)>subject.ini

#now we make the actual input file for iadhore which points to all of these files.
cd ../
cat query/query.ini subject/subject.ini |tr "\t" " " >iadhore.ini

```
Now you have the input file for iadhore that needs some manual modifications to work. Currently it looks as such.
```
1 query/1.lst
2 query/2.lst
3 query/3.lst
4 query/4.lst
5 query/5.lst
6 query/6.lst
7 query/7.lst
8 query/8.lst
9 query/9.lst
10 query/10.lst
etc.
9183 query/9183.lst
9185 query/9185.lst
9186 query/9186.lst
9192 query/9192.lst
000001 subject/000001.lst
1syntmer subject/1syntmer.lst
000002 subject/000002.lst
2syntmer subject/2syntmer.lst
000003 subject/000003.lst
3syntmer subject/3syntmer.lst
4syntmer subject/4syntmer.lst
5syntmer subject/5syntmer.lst
6syntmer subject/6syntmer.lst
7syntmer subject/7syntmer.lst
000008 subject/000008.lst
8syntmer subject/8syntmer.lst
etc.
```
We need to add some relevant information to change this file for iadhore
```
#this is what is put in the iadhore.ini file
genome=query
1 query/1.lst
2 query/2.lst
3 query/3.lst
4 query/4.lst
5 query/5.lst
6 query/6.lst
7 query/7.lst
8 query/8.lst
9 query/9.lst
10 query/10.lst
etc...
#empty newline
genome=subject
000001 subject/000001.lst
1syntmer subject/1syntmer.lst
000002 subject/000002.lst
2syntmer subject/2syntmer.lst
000003 subject/000003.lst
3syntmer subject/3syntmer.lst
4syntmer subject/4syntmer.lst
#empty newline
prob_cutoff=0.001
anchor_points=3
number_of_threads=16
visualizeAlignment=true
blast_table= OrthologousPairs.list
output_path= output
alignment_method=gg2
gap_size=15
cluster_gap=20
level_2_only=false
q_value=.05
```