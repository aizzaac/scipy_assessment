# Revelo's Assessment

Do **NOT** open pull requests to this repository. If you do, your application will be immediately discarded.

## Thoughts

- 4h05: Read assessment instructions
- 4h07: Clone git and build Docker image
- 4h10: Analyze errors
- 4h15: Fix JSONArgsRecommended warning
  From this: CMD pytest -v -rA --tb=long -p no:cacheprovider --disable-warnings \
    scipy/sparse/tests/test_base.py
  To this: CMD ["pytest", "-v", "-rA", "--tb=long", "-p", "no:cacheprovider", "--disable-warnings", "scipy/sparse/tests/test_base.py"]
- 4h18: Search where is the error (update or install)?
  RUN apt-get update

  RUN echo "--- Iniciando apt-get install build-essential ---" && \
	    apt-get install -y build-essential
	
	RUN echo "--- Iniciando apt-get install gfortran ---" && \
	    apt-get install -y gfortran
	
	RUN echo "--- Iniciando apt-get install libopenblas-dev ---" && \
	    apt-get install -y libopenblas-dev
	
	RUN echo "--- Iniciando apt-get install liblapack-dev ---" && \
	    apt-get install -y liblapack-dev
	
	RUN echo "--- Iniciando apt-get install git ---" && \
	    apt-get install -y git
	
	RUN echo "--- Limpiando listas de apt ---" && \
    rm -rf /var/lib/apt/lists/*

- 4h23: Check if file setup.py exist, its content, etc
  RUN find /usr/src/app -name setup.py
  RUN grep -r "ISRELEASED = False" /usr/src/app

- 4h28: Copy setup.py and fix sintax of "sed
  COPY setup.py /usr/src/app
  RUN sed -i "s/ISRELEASED = False/ISRELEASED = True/" setup.py
  RUN sed -i "/test_suite/d" setup.py

- 4h32: Build Docker image
- 4h45: Run container and mount a volume
- 4h50: Start TDD
