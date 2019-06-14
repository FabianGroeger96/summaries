all:
	pandoc *.md -o cheatsheet.pdf --template="../../_helpers/template_cheatsheet.tex" --top-level-division=section variables.yaml

clean:
	rm -f cheatsheet.pdf

rebuild: clean all
