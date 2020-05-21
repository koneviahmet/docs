# pdfmake
nodejs üzerinden pdf oluşturucu sevdim gibi bakalım

kurulumu
> npm i --save pdfmake

## text
text te font ve style atayabiliyorsun şahane görünüyor.

text için örnek
```js
var fonts = {
	Roboto: {
		normal: 'fonts/Roboto-Regular.ttf',
		bold: 'fonts/Roboto-Medium.ttf',
		italics: 'fonts/Roboto-Italic.ttf',
		bolditalics: 'fonts/Roboto-MediumItalic.ttf'
	},
  Helvetica: {
  normal: 'Helvetica',
  bold: 'Helvetica-Bold',
  italics: 'Helvetica-Oblique',
  bolditalics: 'Helvetica-BoldOblique'
},
};

var PdfPrinter = require('pdfmake');
var printer = new PdfPrinter(fonts);
var fs = require('fs');


var docDefinition = {
	content: [
    'Normal sıradan bir text',
		{ text: 'font size belirlenmiş bir text', fontSize: 8},
    { text: 'ben başlığım sitilim aşağıda belirlendi', style: 'header' },
    { text: 'Another text', style: 'anotherStyle' },
    { text: 'Multiple styles applied', style: [ 'header', 'anotherStyle' ] }

  ],
  defaultStyle: {
    font: 'Roboto'
  },

  /* style ekle*/
  styles: {
    header: {
      fontSize: 22,
      bold: true
    },
    anotherStyle: {
      italics: true,
      alignment: 'right'
    }
  },

  /* varsayılan style */
  defaultStyle: {
    fontSize: 12,
    bold: false
  }
};


var pdfDoc = printer.createPdfKitDocument(docDefinition);
pdfDoc.pipe(fs.createWriteStream('pdfs/bir.pdf'));
pdfDoc.end();

```



## columns
kolon oluşturmak için

```js
{
  columns: [
    {
      // auto-sized columns have their widths based on their content
      width: 'auto',
      text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.'
    },
    {
      // star-sized columns fill the remaining space
      // if there's more than one star-column, available width is divided equally
      width: '*',
      text: ' Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum. '
    }
  ],
  // optional space between columns
  columnGap: 25
}
```

## table
tablo oluşturmak için
colSpan diye aratırsan colspan ve row span nasıl yapılacak anlatıyor

```js
content: [
	{
		layout: 'lightHorizontalLines', // optional
		table: {
			// headers are automatically repeated if the table spans over multiple pages
			// you can declare how many rows should be treated as headers
			headerRows: 1,
			widths: [ '*', 'auto', 100, '*' ],
			body: [
				[ 'First', 'Second', 'Third', 'The last one' ],
				[ 'Value 1', 'Value 2', 'Value 3', {}],
				[ 'Value 1', 'Value 2', 'Value 3', 'Value 4' ],
				[ 'Value 1', 'Value 2', 'Value 3', 'Value 4' ],
				[ { text: 'Bold value', bold: true }, 'Val 2', 'Val 3', 'Val 4' ]
			]
		}
	},


]
```

## yeni sayfa
```js
content: [
	'deneme medey',
	{
		text: '',
		fit: [100, 100],
		pageBreak: 'after'
	},
	'deneme 2'
]
```


vs... bütün örnekler burada mevcut
https://pdfmake.github.io/docs/document-definition-object/tables/
