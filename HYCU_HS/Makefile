####################################################################################################
#
#	Created by S+core IDE V2.6.1		04:23:19	03/23/13
#
####################################################################################################

OUTDIR	= Debug
APPDIR	= C:\Sunplus\S_CORE~1.1

TOOLDIR	= C:\Sunplus\S_CORE~1.1\gnu\bin
INCLUDES =  -I"C:/Users/Administrator/Documents/GitHub/HYCU/HYCU_HS/"
LIBFOLDER = 

CC	= "$(TOOLDIR)\score-elf-gcc"
CPP	= "$(TOOLDIR)\score-elf-g++"
AS	= "$(TOOLDIR)\score-elf-as"
AR	= "$(TOOLDIR)\score-elf-ar"
LD	= "$(TOOLDIR)\score-elf-ld"
NM	= "$(TOOLDIR)\score-elf-nm"
RM	= "$(TOOLDIR)\rm"

OBJCOPY	= "$(TOOLDIR)\score-elf-objcopy"
OBJDUMP	= "$(TOOLDIR)\score-elf-objdump"
LDSCRIPT	= "C:\Users\Administrator\Documents\GitHub\HYCU\HYCU_HS\HYCU_Prog.ld"

CCDEFFLAG	= -mscore7 -mel -g -Wall
CCADDFLAG	= 
ASDEFFLAG	= -Wa,-gdwarf-2  -x assembler-with-cpp
ASADDFLAG	= 
LDDEFFLAG	= -T$(LDSCRIPT)   -lm -lc -lgcc
LDADDFLAG	= -Wl,-Map,$@.map
RESDEFFLAG	= -EL -Tresource.ld  -b binary
RMFLAG		= -rf

BINFILE		= "$(OUTDIR)\HYCU.elf"


RESFILES	=

OBJFILES	=\
	"$(OUTDIR)\HYCU_startup.o"\
	"$(OUTDIR)\main.o"\
	"$(OUTDIR)\libgloss.o"

"$(OUTDIR)\libgloss.o" "$(OUTDIR)\libgloss.d": "C:\Users\Administrator\Documents\GitHub\HYCU\HYCU_HS\libgloss.c"
	@echo libgloss.c
	@$(CC) -c $(CCDEFFLAG) $(CCADDFLAG) -B $(TOOLDIR) $(INCLUDES) -MMD -MP -MF"$(OUTDIR)\libgloss.d" -MT"$(OUTDIR)\libgloss.d" -o "$(OUTDIR)\libgloss.o" "C:\Users\Administrator\Documents\GitHub\HYCU\HYCU_HS\libgloss.c" 

"$(OUTDIR)\main.o" "$(OUTDIR)\main.d": "C:\Users\Administrator\Documents\GitHub\HYCU\HYCU_HS\main.c"
	@echo main.c
	@$(CC) -c $(CCDEFFLAG) $(CCADDFLAG) -B $(TOOLDIR) $(INCLUDES) -MMD -MP -MF"$(OUTDIR)\main.d" -MT"$(OUTDIR)\main.d" -o "$(OUTDIR)\main.o" "C:\Users\Administrator\Documents\GitHub\HYCU\HYCU_HS\main.c" 

"$(OUTDIR)\HYCU_startup.o" "$(OUTDIR)\HYCU_startup.d": "C:\Users\Administrator\Documents\GitHub\HYCU\HYCU_HS\HYCU_startup.s"
	@echo HYCU_startup.s
	@$(CC) -c $(CCDEFFLAG) $(CCADDFLAG) -B $(TOOLDIR) $(INCLUDES) $(ASDEFFLAG) $(ASADDFLAG) -MMD -MP -MF"$(OUTDIR)\HYCU_startup.d" -MT"$(OUTDIR)\HYCU_startup.d" -o "$(OUTDIR)\HYCU_startup.o" "C:\Users\Administrator\Documents\GitHub\HYCU\HYCU_HS\HYCU_startup.s" 


all : "$(OUTDIR)" $(BINFILE)

"$(OUTDIR)" :
	@if not exist "$(OUTDIR)/$(NULL)" mkdir "$(OUTDIR)"

LINKLIB	= 

$(BINFILE) : $(RESFILES) $(OBJFILES) $(LINKLIB) $(LDSCRIPT) "C:\Users\Administrator\Documents\GitHub\HYCU\HYCU_HS\Resource.h"
			@echo linking...
			@$(CC) $(CCDEFFLAG) $(CCADDFLAG) -B$(TOOLDIR) "Obj.lst" -o $(BINFILE) "Lib.lst" $(LIBFOLDER) $(LDDEFFLAG) $(LDADDFLAG)
			@$(OBJCOPY) -O binary $@ $@.bin
			@echo creat .srec for simulator...
			@$(OBJCOPY) -O srec $@  $@.srec
.PHONY: clean
clean :
	@$(RM) $(RMFLAG) ".\HYCU_HS.fms"
DEPFILES	=\
	"$(OUTDIR)\HYCU_startup.d"\
	"$(OUTDIR)\main.d"\
	"$(OUTDIR)\libgloss.d"

ifneq ($(wildcard $(DEPFILES)),)
include $(DEPFILES)
endif

