ico_sizes = 16 32 48 128 256

.PHONY: logo thumbnails clean

logo: thumbnails favicon.ico

thumbnails: images/my-192x192.png images/my-512x512.png

images/my-192x192.png: images/my.svg
	inkscape images/my.svg -o images/my-192x192.png -w 192 2> /dev/null

images/my-512x512.png: images/my.svg
	inkscape images/my.svg -o images/my-512x512.png -w 512 2> /dev/null

favicon.ico: images/my.svg
	@for size in ${ico_sizes}; do \
		echo "inkscape: images/my.svg -> $${size}.png"; \
		inkscape images/my.svg -o $$size.png -w $$size 2> /dev/null; \
	done
	convert $(patsubst %, %.png, ${ico_sizes}) favicon.ico
	rm -f $(patsubst %, %.png, ${ico_sizes})

clean: 
	rm -f favicon.ico images/my-*.png
