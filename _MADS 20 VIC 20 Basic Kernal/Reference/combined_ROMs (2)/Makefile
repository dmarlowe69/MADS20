
combined_ROMs.bin: combined_ROMs.asm
	xa -M -o $@ -l $(basename $@).sym $<

combined_ROMs.sym: combined_ROMs.bin

combined_ROMs.inc: combined_ROMs.sym
	awk -F, '$$1 !~ "^LAB_" {print $$2, $$1}' $< | sort -n | awk '{printf "%12s = $$%s\n",  $$2, substr($$1,3)}' >$@

test: combined_ROMs.bin
	diff $< original.bin

clean:
	rm -f combined_ROMs.bin combined_ROMs.sym combined_ROMs.inc
