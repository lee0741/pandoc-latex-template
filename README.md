# Pandoc LaTeX Template

This is a [Pandoc](https://pandoc.org/) LaTeX template to convert Markdown files to PDFs.

## Usage

1. Install [Pandoc](https://pandoc.org/installing.html) and [LaTeX](https://en.wikibooks.org/wiki/LaTeX/Installation#Distributions).
2. Clone this repository.
3. Check Pandoc's templates folder by running `pandoc --version`.
4. Move `normal.latex` to Pandoc's templates folder.
5. Run `pandoc` with the provided template: `pandoc input.md -o output.pdf --template normal --pdf-engine=xelatex`

## Shell Function

```sh
md2pdf() {
    if [ -z "$1" ]; then
        echo "Usage: md2pdf <input.md>"
        return 1
    fi

    input_file="$1"

    # Check if file exists
    if [ ! -f "$input_file" ]; then
        echo "Error: File '$input_file' not found!"
        return 1
    fi

    # Extract filename without extension
    output_file="${input_file%.md}.pdf"

    # Run Pandoc command
    pandoc "$input_file" -o "$output_file" --template normal --pdf-engine=xelatex

    # Check if PDF was created successfully
    if [ -f "$output_file" ]; then
        echo "✅ PDF generated: $output_file"
    else
        echo "❌ Error: Failed to generate PDF!"
        return 1
    fi
}
```

1. Copy and paste the function into your shell configuration file.
2. Reload your shell.
3. Run the function: `md2pdf input.md`

## License

[MIT](https://opensource.org/licenses/MIT)
