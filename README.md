# Fast Text Search

This repository contains my implementation of a fast semantic text search engine which can search ~1 million chunked texts in below 1s.

## Overview

In this solution, firstly i use [MongoDB/cosmopedia-wikihow-chunked](https://huggingface.co/datasets/MongoDB/cosmopedia-wikihow-chunked) as a dataset to benchmark my approach, secondly i used a simple language model called [all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2) from [SBert](https://sbert.net/) library and embed all texts, lastly i used [Spotify Voyager](https://github.com/spotify/voyager) as embedding search engine and saved the voyager db on disk so i don't need to recalculate embeddings again next time.
sadly generating embedding on CPU takes a lot of time and the file size of generated embeddings is around 400MB so i couldn't upload it here but if you want to test this solution you can use a Google colab GPU which embeds all 1 million rows in around 10 minutes.

## Results

Calculating embedding of the corpus takes some time but you just have to do it once, The interesting part is that after calculation, search on them using Voyager is very fast (In my benchmarks it's below 500ms).

## Future Improvements

-   Using quantized Language Models to embed texts faster
-   Using multi-language models
-   Use other engines too, like [https://github.com/facebookresearch/faiss](FAISS) and [https://github.com/unum-cloud/usearch](USearch)
-   Integrate quantization on search for even faster search
-   Add re-ranking capabilities (it need a cross-encoder based model)

## Contributing

Feel free to fork this repository and submit pull requests with any improvements or suggestions.
