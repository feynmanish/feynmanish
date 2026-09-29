## Arkadi Sachnowitsch

AI engineer in Munich. I build retrieval systems — RAG, embeddings, hybrid search, information extraction — and I measure them.

### Atlandex · [atlandex.app](https://atlandex.app)

A production RAG/NLP system over long-form video and books. Sole engineer, live since 2023. Product code is private; happy to walk through it.

**Retrieval.** A labelled 22-query evaluation set, re-runnable across configurations, so a change to chunking, embedding model or fusion strategy produces a measured delta. Dense retrieval (FAISS/L2) reaches recall@3 0.93 and nDCG@3 0.88; reciprocal-rank fusion with a TF-IDF baseline reaches recall@3 1.0. The dense-only misses were vocabulary mismatch, not semantics.

**Pipeline.** 400+ hours of transcript chunked on chapter boundaries with a token-budget split. LLM and embedding providers behind a single interface (DeepInfra, AWS Bedrock). Vectors in PostgreSQL, FAISS at query time. The same extract-and-merge pipeline runs over full-length books with chapter-scoped evidence spans. A vision-model pipeline reads text out of images, structures it, and persists it through background jobs.

**Serving.** Flask APIs exposing retrieval and extraction, with SSE streaming. Snippet-seek p95 17.0s → 4.5s via indexed Postgres; time-to-first-term 1.7s p50. Parallelized per-chapter extraction p50 30.0s → 14.8s at roughly $0.0001 per window. Three client surfaces on one backend: React web app, React Native app on Google Play, published Chrome extension.

**Around it.** pytest and GitHub Actions on every PR. Gunicorn + RQ/Redis on Heroku; the Python backend packaged as a Docker image.

### Before that

A geospatial web app (2019–2023) on PostgreSQL, Node/Express and REST APIs — PostGIS, geocoding and Google Maps for route storage and location recommendations. Live with real users.

### Stack

Python · Flask · PostgreSQL · FAISS · AWS (S3, Bedrock) · GCP Vision · Docker · TypeScript · React · React Native · Node/Express

### Contact

Munich · [arkadi.dvdy@gmail.com](mailto:arkadi.dvdy@gmail.com) · [LinkedIn](https://www.linkedin.com/in/arkadi-sachnowitsch-95166537b) · German / English / Russian
