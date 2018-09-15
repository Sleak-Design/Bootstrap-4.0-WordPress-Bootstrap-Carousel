



		# Bootstrap-4.0-WordPress-Bootstrap-Carousel
		For output in template file :

		<div id="carouselExampleIndicators" class="carousel slide" data-ride="carousel">
		<ol class="carousel-indicators">
		  <li data-target="#carouselExampleIndicators" data-slide-to="0" class="active"></li>
		  <li data-target="#carouselExampleIndicators" data-slide-to="1"></li>
		  <li data-target="#carouselExampleIndicators" data-slide-to="2"></li>
		</ol>
			 <!-- Wrapper for slides -->
			<div class="carousel-inner" role="listbox">
			<?php $slider = get_posts(array('post_type' => 'slider', 'posts_per_page' => 5)); ?>
			  <?php $count = 0; ?>
			  <?php foreach($slider as $slide): ?>
			  <div class="carousel-item <?php echo ($count == 0) ? 'active' : ''; ?>">
				<img src="<?php echo wp_get_attachment_url( get_post_thumbnail_id($slide->ID)) ?>" class="img-fluid"/>
			  </div>
			  <?php $count++; ?>
			<?php endforeach; ?>
			</div>
		 <a class="carousel-control-prev" href="#carouselExampleIndicators" role="button" data-slide="prev">
		  <span class="carousel-control-prev-icon" aria-hidden="true"></span>
		  <span class="sr-only">Previous</span>
		</a>
		<a class="carousel-control-next" href="#carouselExampleIndicators" role="button" data-slide="next">
		  <span class="carousel-control-next-icon" aria-hidden="true"></span>
		  <span class="sr-only">Next</span>
		</a>
		</div>
