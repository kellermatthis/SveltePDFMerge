<script>	
    let files;
    import PDFMerger from 'pdf-merger-js/browser';

    var merger = new PDFMerger();
    $: if (files) {


        (async () => {
            for (let i = 0; i < files.length; i++) {
                await merger.add(files[i]);
                
            }
            await merger.save(files[0].name + '_merged.pdf');
        })();
	}
</script>

<p>Select the PDFs you want to merge:</p>
<input
	bind:files
	id="many"
	multiple
	type="file"
    accept=".pdf"
/>