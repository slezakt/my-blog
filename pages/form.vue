<template>
	<div>
		<form name="contact" method="POST" data-netlify="true">
			<label for="">Label</label>
			<input type="text" name="name">
			<div data-netlify-recaptcha="true"></div>
			<input type="hidden" name="form-name" value="contact" />
			<input type="submit" value="Odeslat">
		</form>
	</div>
</template>